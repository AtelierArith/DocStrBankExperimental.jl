```
ITensor([::Type{ElT} = Float64,] ::UndefInitializer, flux::QN, inds)
ITensor([::Type{ElT} = Float64,] ::UndefInitializer, flux::QN, inds::Index...)
```

インデックス `inds` と未定義要素の型 `ElT` を持つ BlockSparse ストレージを持つ ITensor を構築します。非ゼロ（割り当てられた）ブロックは、提供された QN `flux` によって決定されます。このコンストラクタを使用する目的の一つは、要素を未定義の方法で初期化する方が、ゼロなどの設定値で初期化するよりも速いということです。

ストレージは `NDTensors.BlockSparse` 型になります。

# 例

```julia
i = Index([QN(0)=>1, QN(1)=>2], "i")
A = ITensor(undef,QN(0),i',dag(i))
B = ITensor(Float64,undef,QN(0),i',dag(i))
C = ITensor(ComplexF64,undef,QN(0),i',dag(i))
```
