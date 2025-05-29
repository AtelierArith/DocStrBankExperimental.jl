```
difference_of_convex_proximal_point!(M, grad_h, p; cost=nothing, kwargs...)
difference_of_convex_proximal_point!(M, mdcpo, p; cost=nothing, kwargs...)
difference_of_convex_proximal_point!(M, mdcpo, prox_g, p; cost=nothing, kwargs...)
```

Compute the difference of convex algorithm to minimize

$$
    \operatorname*{arg\,min}_{p∈\mathcal M} g(p) - h(p)
$$

where you have to provide the proximal map of `g` and the gradient of `h`.

The computation is done in-place of `p`.

For all further details, especially the keyword arguments, see [`difference_of_convex_proximal_point`](@ref).
