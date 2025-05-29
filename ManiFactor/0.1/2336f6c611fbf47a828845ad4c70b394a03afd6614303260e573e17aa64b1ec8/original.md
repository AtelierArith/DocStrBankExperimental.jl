```
function approximate(
    m::Int,
    M::AbstractManifold,
    f::Function; # :: [-1, 1]^m -> M^n
    p=[], # Point to linearize around. Default is Karcher mean of 100 samples.
    base_approximate=approximate_vector::Function, # :: (m::Int) -> (n::Int) -> ([-1, 1]^m -> R^n) -> ([-1, 1]^m -> R^n)
    kwargs...
    )::Function # :: [-1, 1]^m -> M^n
```

Approximate a manifold-valued function using Riemann normal coordinate chart.
