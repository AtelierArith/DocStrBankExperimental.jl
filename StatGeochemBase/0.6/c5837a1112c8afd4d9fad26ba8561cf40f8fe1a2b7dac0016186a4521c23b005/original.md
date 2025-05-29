```julia
renormalize!(A::AbstractArray; dim, total=1.0)
```

Normalize an array `A` in place such that it sums to `total`. Optionally may specify a dimension `dim` along which to normalize.
