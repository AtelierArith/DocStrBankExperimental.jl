naivemoment(data::Matrix{Float}, m::Int)

Returns Array{Float, m} the m'th moment tensor

```jldoctest
julia> M =  [[-0.88626   0.279571];[-0.704774  0.131896]];

julia> naivemoment(M, 3)
2×2×2 Array{Float64,3}:
[:, :, 1] =
  -0.523092   0.142552
  0.142552  -0.0407653

[:, :, 2] =
  0.142552   -0.0407653
  -0.0407653   0.0120729

```
