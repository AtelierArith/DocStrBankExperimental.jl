```
Strang([T=Int,] n::Int)
```

要素の型 `T` を持つ `Strang` 行列を構築します。この特別な行列はギルバート・ストラングにちなんで名付けられたもので、対称、三重対角、トポリッツです。 [Julia paper](https://doi.org/10.1137/141000671) の図1を参照してください。

```jldoctest
julia> Strang(4)
4×4 Strang{Int64}:
  2  -1   0   0
 -1   2  -1   0
  0  -1   2  -1
  0   0  -1   2

julia> Strang(Int16, 3)
3×3 Strang{Int16}:
  2  -1   0
 -1   2  -1
  0  -1   2
```
