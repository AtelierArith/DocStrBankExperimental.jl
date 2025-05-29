naivecumulant(data::Matrix, m::Int)

Returns Array{Float, m} the m'th cumulant tensor

```jldoctest
julia> M =  [[-0.88626   0.279571];[-0.704774  0.131896]];

julia> naivecumulant(M, 3)
2×2×2 Array{Float64,3}:
[:, :, 1] =
 0.0  0.0
 0.0  0.0

[:, :, 2] =
 0.0  0.0
 0.0  0.0

```
