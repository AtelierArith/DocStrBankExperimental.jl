```julia
struct InfiniteSquare <: MPSKitModels.AbstractLattice{2}
```

無限の正方格子で、サイズが `(Nrows, Ncols)` の単位セルを持ちます。

## フィールド

  * `Nrows::Int64`
  * `Ncols::Int64`

## コンストラクタ

```
InfiniteSquare([Nrows=1, Ncols=1])
```

デフォルトでは、(1, 1) の単位セルを持つ無限の正方形が構築されます。
