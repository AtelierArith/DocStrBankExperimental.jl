```
ITensor([ElT::Type, ]x::Number, flux::QN, inds)
ITensor([ElT::Type, ]x::Number, flux::QN, inds::Index...)
```

QNフラックス`flux`が`x`に設定されたすべての要素が一貫性のあるITensorを構築します。インデックスは`inds`です。

もし`x`が`Int`または`Complex{Int}`であれば、要素は最初の入力で指定されていない限り`float(x)`に設定されます。

ストレージは`NDTensors.BlockSparse`型になります。

# 例

```julia
i = Index([QN(0)=>1, QN(1)=>2], "i")
A = ITensor(2.3, QN(0), i', dag(i))
B = ITensor(Float64, 3.5, QN(0), i', dag(i))
C = ITensor(ComplexF64, 4, QN(0), i', dag(i))
```

!!! 警告     将来のバージョンでは、整数入力を`float`で自動的に変換しない可能性があり、その場合、特定の要素型に依存しない方が良いでしょう。
