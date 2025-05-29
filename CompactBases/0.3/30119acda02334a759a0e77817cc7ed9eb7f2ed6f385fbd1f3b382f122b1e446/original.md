```
FunctionProduct{Conjugated}(L, R[, T; w=one]) where {Conjugated,T}
```

Construct a [`FunctionProduct`](@ref) for computing the product of two functions expanded over `L` and `R`, respectively:

$$
h(x) = f^\circ(x)g(x)w(x)
$$

where $w(x)$ is an optional weight function, over the basis of $g(x)$, via Vandermonde interpolation.
