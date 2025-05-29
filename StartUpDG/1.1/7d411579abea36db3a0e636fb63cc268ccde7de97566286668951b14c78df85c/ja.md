```
struct RefElemData
```

RefElemData: 与えられた基準要素に対する高次ノード基底のための情報（補間点、体積/面の数値積分、演算子）を含みます。

例:

```julia
N = 3
rd = RefElemData(Tri(), N)
(; r, s ) = rd
```
