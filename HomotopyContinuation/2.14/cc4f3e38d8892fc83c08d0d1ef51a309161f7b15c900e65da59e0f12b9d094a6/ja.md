```
coord_change(A::LinearSubspace, C₁::Coordinates, C₂::Coordinates, p)
```

与えられた（アフィン）線形部分空間 `A` と座標 `C₁` における点 `p` に対して、座標 `C₂` における点 `x` を計算します。

## 例

```julia-repl
julia> A = LinearSubspace([1 0 3; 2 1 3], [5, -2]);

julia> u = [1.25];

julia> x = coord_change(A, Intrinsic, Extrinsic, u)
3-element Array{Float64,1}:
 -3.9129405809619744
 -3.087059419038025
  2.9709801936539915

julia> A(x, Extrinsic)
2-element Array{Float64,1}:
 0.0
 0.0

julia> x - A(u, Intrinsic)
3-element Array{Float64,1}:
 0.0
 0.0
 0.0
```
