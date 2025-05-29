```
emptyITensor([::Type{ElT} = NDTensors.EmptyNumber, ]inds)
emptyITensor([::Type{ElT} = NDTensors.EmptyNumber, ]inds::Index...)
```

`NDTensors.EmptyStorage` ストレージタイプ、インデックス `inds`、および要素タイプ `ElT` を持つ ITensor を構築します。要素タイプが指定されていない場合、デフォルトで `NDTensors.EmptyNumber` になり、これは任意の値を取ることができる数値タイプを表します（例えば、設定された最初の値のタイプなど）。
