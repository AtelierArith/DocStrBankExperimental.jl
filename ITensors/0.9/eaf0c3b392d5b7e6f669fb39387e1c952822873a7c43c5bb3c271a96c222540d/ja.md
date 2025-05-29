```
random_itensor([::Type{ElT} = Float64, ][flux::QN = QN(), ]inds)
random_itensor([::Type{ElT} = Float64, ][flux::QN = QN(), ]inds::Index...)
```

`ElT`の型のランダムな要素で満たされた`NDTensors.BlockSparse`ストレージを持つITensorを構築します。非ゼロブロックは`flux`によって決定されます。

`ElT`が指定されていない場合、デフォルトは`Float64`です。フラックスが指定されていない場合、デフォルトは`QN()`です。
