```
projection_gradient_on_set(::DefaultDistance, v::AbstractVector{T}, sets::AbstractVector{<:MOI.AbstractSet})
```

Derivative of the projection of vector `v` on product of `sets` projection*gradient*on*set[i,j] = ∂projection*on*set[i] / ∂v[j] where `projection*on_set`denotes projection of`v`on`cone`

Find expression of projections on cones and their derivatives here: https://stanford.edu/~boyd/papers/pdf/cone*prog*refine.pdf
