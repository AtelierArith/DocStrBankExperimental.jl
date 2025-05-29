```
isless(p::FreeAssociativeAlgebraElem{T}, q::FreeAssociativeAlgebraElem{T}) where T
```

Implements the degree lexicographic ordering on terms, i.e. first, the degrees of the largest monomials are compared, and if they are the same, they are compared lexicographically and if they are still the same, the coefficients are compared.  If everything is still the same, the next largest monomial is compared and lastly the number of monomials is compared. Since the coefficients are also compared, this only works when the  coefficient Ring implements isless.

The order of letters is the reverse of the order given when initialising the algebra.

# Examples

```jldoctest
julia> R, (x, y) = free_associative_algebra(QQ, ["x", "y"]);

julia> x < y^2
true

julia> x^2 < x^2 + y
true

julia> y < x
true

julia> x^2 < 2*x^2
true
```
