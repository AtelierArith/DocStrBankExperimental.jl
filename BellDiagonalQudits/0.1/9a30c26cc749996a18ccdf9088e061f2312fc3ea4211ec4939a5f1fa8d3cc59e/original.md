```
create_random_bounded_ews(
    d,
    standardBasis::StandardBasis,
    n,
    sphericalOnly::Bool,
    iterations::Integer,
    method=Optim.NelderMead,
    useConstrainedOpt=false
)
```

Return array of `n` `BoundedEW` with $d^2$ `standardBasis` coordinates uniformly distributed in [-1, 1] if `sphericalOnly` is false or uniformly distributed on unit sphere otherwise.

Use `iterations` runs to improve optimizatio with Optim.jl optimization method `method`.
