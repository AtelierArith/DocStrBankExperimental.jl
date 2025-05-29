```
function OT!(
    D::AbstractDivergence,
    C,
    a::DiscreteMeasure,
    b::DiscreteMeasure,
    ϵ = 1e-1;
    C = (x, y) -> norm(x - y),
    kwargs...,
) -> Number
```

Computes the optimal transport cost between `a` and `b`, using [`unbalanced_sinkhorn!`](@ref); see that function for the meaning of the parameters and the keyword arguments. Implements Equation (15) of [[SFVTP19](@ref)].
