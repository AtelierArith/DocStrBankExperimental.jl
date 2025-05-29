```
monomials(p::AbstractPolynomialLike)
```

Returns an iterator over the monomials of `p` of the nonzero terms of the polynomial sorted in the decreasing order.

```
monomials(vars::Union{Vector{<:AbstractVariable},Tuple}, degs::AbstractVector{Int}, filter::Function = m -> true)
```

Builds the vector of all the monomial_vector `m` with variables `vars` such that the degree `degree(m)` is in `degs` and `filter(m)` is `true`.

See also [`ExponentsIterator`](@ref).

### Examples

Calling `monomials` on $4x^2y + xy + 2x$ should return an iterator of $[x^2y, xy, x]$.

Calling `monomials((x, y), [1, 3], m -> degree(m, y) != 1)` should return `[x^3, x*y^2, y^3, x]` where `x^2*y` and `y` have been excluded by the filter.
