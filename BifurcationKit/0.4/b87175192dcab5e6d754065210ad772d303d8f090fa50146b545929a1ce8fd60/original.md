```julia
continuation(
    prob,
    x0,
    par0,
    x1,
    p1,
    alg,
    lens,
    contParams;
    bothside,
    kwargs...
)

```

[Internal] This function is not meant to be called directly.

This function is the analog of [`continuation`](@ref) when the first two points on the branch are passed (instead of a single one). Hence `x0` is the first point on the branch (with pseudo arc length `s=0`) with parameter `par0` and `x1` is the second point with parameter `set(par0, lens, p1)`.
