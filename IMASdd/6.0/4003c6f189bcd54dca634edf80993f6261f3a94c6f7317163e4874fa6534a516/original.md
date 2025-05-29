```
gradient(coord1::AbstractVector, coord2::AbstractVector, mat::Matrix; method::Symbol=:second_order)
```

Finite difference method of the gradient: [:backward, :central, :forward, :second*order, :third*order]

Computes the gradient in both dimensions
