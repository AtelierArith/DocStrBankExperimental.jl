```
struct Polynomial{N,T}
```

A polynomial in `N` variables with coefficients of type `T`.

The functor interface is implemented, so that `p(x)` evaluates the polynomial. For performance reasons, `x` is expected to be a `Tuple`.

# Examples

A polynomial with a single term can be created by passing a pair mapping the order to the coefficient:

```jldoctest; output = false
julia> Polynomial((1,1)=>2)
2xy
```

When multiple terms are present, they must be passed as vector (or tuple) of pairs:

```jldoctest
julia> Polynomial([(1,1)=>2, (0,1)=>-1])
-y + 2xy
```

The spatial dimension is automatically inferred from the length of the order tuple:

```jldoctest
julia> Polynomial((1,1,1)=>2)
2xyz
```
