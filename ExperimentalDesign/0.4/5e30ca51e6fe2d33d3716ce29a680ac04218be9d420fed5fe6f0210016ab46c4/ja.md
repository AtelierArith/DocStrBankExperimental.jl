```julia
ccdesign(n::Int64) -> Any
ccdesign(n::Int64, center::Array{Int64}) -> Any
ccdesign(
    n::Int64,
    center::Array{Int64},
    alpha::Symbol
) -> Any
ccdesign(
    n::Int64,
    center::Array{Int64},
    alpha::Symbol,
    face::Symbol
) -> Any

```

中央合成デザインを構築します。

```jldoctest
julia> ccdesign(3)
22×3 Matrix{Float64}:
 -1.0      -1.0      -1.0
  1.0      -1.0      -1.0
 -1.0       1.0      -1.0
  1.0       1.0      -1.0
 -1.0      -1.0       1.0
  1.0      -1.0       1.0
 -1.0       1.0       1.0
  1.0       1.0       1.0
  0.0       0.0       0.0
  0.0       0.0       0.0
  ⋮
  1.82574   0.0       0.0
  0.0      -1.82574   0.0
  0.0       1.82574   0.0
  0.0       0.0      -1.82574
  0.0       0.0       1.82574
  0.0       0.0       0.0
  0.0       0.0       0.0
  0.0       0.0       0.0
  0.0       0.0       0.0

```
