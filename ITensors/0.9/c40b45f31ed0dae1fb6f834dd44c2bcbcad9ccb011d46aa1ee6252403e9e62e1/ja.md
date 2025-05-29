```
emptyITensor([::Type{ElT} = EmptyNumber, ]inds)
emptyITensor([::Type{ElT} = EmptyNumber, ]inds::QNIndex...)
```

`ElT`の要素型を持つ`NDTensors.BlockSparse`ストレージのITensorをブロックなしで構築します。

`ElT`が指定されていない場合、デフォルトは`NDTensors.EmptyNumber`です。
