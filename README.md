# ONNX Models

This is a repository for storing ONNX models.

### Models

- [BVLC AlexNet](bvlc_alexnet)

- [DenseNet-121](densenet121)

- [Inception-v1](inception_v1)

- [Inception-v2](inception_v2)

- [ResNet-50](resnet50)

- [ShuffleNet](shufflenet)

- [SqueezeNet](squeezenet)

- [VGG-16](vgg16)

- [VGG-19](vgg19)

### Usage

Every ONNX backend should support running these models out of the box. After dowloading and extracting the tarball of each model, there should be

- A protobuf file `model.pb` which is the serialized ONNX model.
- Several sets of sample inputs and outputs files (`test_data_*.npz`), they are numpy serialized archive.

e.g. they can be used like this:

```python
import numpy as np
import onnx
import onnx_backend as backend

# Load the model and sample inputs and outputs
model = onnx.load(model_pb_path)
sample = np.load(npz_path, encoding='bytes')
inputs = list(sample['inputs'])
outputs = list(sample['outputs'])

# Run the model with an onnx backend and verify the results
np.testing.assert_almost_equal(outputs, backend.run_model(model, inputs))
```

# License

[MIT License](LICENSE)
