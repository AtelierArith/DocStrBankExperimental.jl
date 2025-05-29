```julia
boxbehnken(
    matrix_size::Int64
) -> LinearAlgebra.Transpose{T, Matrix{T1}} where {T, T1}

```

Constructs a Box-Behnken design with size `matrix_size`.

```jldoctest
julia> boxbehnken(4)
27×4 transpose(::Matrix{Float64}) with eltype Float64:
 -1.0  -1.0   0.0   0.0
  1.0  -1.0   0.0   0.0
 -1.0   1.0   0.0   0.0
  1.0   1.0   0.0   0.0
 -1.0   0.0  -1.0   0.0
  1.0   0.0  -1.0   0.0
 -1.0   0.0   1.0   0.0
  1.0   0.0   1.0   0.0
 -1.0   0.0   0.0  -1.0
  1.0   0.0   0.0  -1.0
  ⋮
  0.0  -1.0   0.0   1.0
  0.0   1.0   0.0   1.0
  0.0   0.0  -1.0  -1.0
  0.0   0.0   1.0  -1.0
  0.0   0.0  -1.0   1.0
  0.0   0.0   1.0   1.0
  0.0   0.0   0.0   0.0
  0.0   0.0   0.0   0.0
  0.0   0.0   0.0   0.0

```
