```
contract_tensors(A::QXTensor, B::QXTensor; mock::Bool=false)
```

Function to contract two QXTensors and return another QXTensor. If the mock flag is false or either of the input tensors use MockTensor then the storage for the final tensor will be of type MockTensor.
