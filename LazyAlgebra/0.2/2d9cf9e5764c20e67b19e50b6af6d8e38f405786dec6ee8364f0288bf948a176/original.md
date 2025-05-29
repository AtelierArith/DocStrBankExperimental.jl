```
vscale!(dst, α, src) -> dst
```

overwrites `dst` with `α*src` and returns `dst`.  Computations are done at the numerical precision of `promote_eltype(src,dst)`.  The source argument may be omitted to perform *in-place* scaling:

```
vscale!(x, α) -> x
```

overwrites `x` with `α*x` and returns `x`.  The convention is that the result is zero-filled if `α=0` (whatever the values in the source).

Methods are provided by default so that the order of the factor `α` and the source vector may be reversed:

```
vscale!(dst, src, α) -> dst
vscale!(α, x) -> x
```

Also see [`vscale`](@ref), [`LinearAlgebra.rmul!](@ref).
