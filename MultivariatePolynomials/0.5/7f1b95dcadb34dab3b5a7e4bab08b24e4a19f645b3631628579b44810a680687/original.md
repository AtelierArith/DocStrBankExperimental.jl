```
function filter_terms(f::Function, p::AbstractPolynomialLike)
```

Filter the polynomial `p` by only keep the terms `t` such that `f(p)` is `true`.

See also [`OfDegree`](@ref).

### Examples

```julia
julia> p = 1 - 2x + x * y - 3y^2 + x^2 * y
1 - 2x - 3y² + xy + x²y

julia> filter_terms(OfDegree(2), p)
-3y² + xy

julia> filter_terms(!OfDegree(2), p)
1 - 2x + x²y

julia> filter_terms(!OfDegree(0:2), p)
x²y

julia> filter_terms(iseven ∘ coefficient, p)
-2x
```
