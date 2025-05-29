```
LatticeValue(lat, values)
```

LatticeValueオブジェクトを構築します。

## 引数

  * `lat`: 値が定義されている格子。
  * `values`: 格子上の値の`AbstractVector`。

## 例

```jldoctest
julia> using LatticeModels

julia> l = SquareLattice(2, 2);

julia> LatticeValue(l, [1, 2, 3, 4])    # カスタム値
LatticeValue{Int64} on a 4-site SquareLattice in 2D space
Values stored in a Vector{Int64}:
[1, 2, 3, 4]

julia> x = LatticeValue(l, :x)          # x座標
LatticeValue{Float64} on a 4-site SquareLattice in 2D space
Values stored in a Vector{Float64}:
[1.0, 1.0, 2.0, 2.0]

julia> l2 = SquareLattice(3, 3);

julia> y = LatticeValue(l2, :y)          # y座標
LatticeValue{Float64} on a 9-site SquareLattice in 2D space
Values stored in a Vector{Float64}:
[1.0, 2.0, 3.0, 1.0, 2.0, 3.0, 1.0, 2.0, 3.0]

julia> x + y
ERROR: Matching lattices expected.
Got following:
  #1: 4-site SquareLattice in 2D space
  #2: 9-site SquareLattice in 2D space
[...]
```
