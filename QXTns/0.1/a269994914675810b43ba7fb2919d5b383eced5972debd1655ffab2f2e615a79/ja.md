```
contract_tensors(A::QXTensor, B::QXTensor; mock::Bool=false)
```

2つのQXTensorを収束させて別のQXTensorを返す関数です。mockフラグがfalseであるか、入力テンソルのいずれかがMockTensorを使用している場合、最終テンソルのストレージはMockTensor型になります。
