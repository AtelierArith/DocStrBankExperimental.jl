```
fidelity(A::ITensor, B::ITensor)
```

2つのITensor間の量子忠実度を計算します。インデックス構造に従って各ITensorをITensorStateとITensorOperatorでラップして、ディスパッチを可能にします。
