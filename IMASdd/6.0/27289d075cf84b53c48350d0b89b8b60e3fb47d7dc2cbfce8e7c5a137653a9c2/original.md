```
gradient(coord1::AbstractVector, coord2::AbstractVector, mat::Matrix, dim::Int; method::Symbol=:second_order)
```

Finite difference method of the gradient: [:backward, :central, :forward, :second*order, :third*order]

Can be applied to either the first (dim=1) or second (dim=2) dimension
