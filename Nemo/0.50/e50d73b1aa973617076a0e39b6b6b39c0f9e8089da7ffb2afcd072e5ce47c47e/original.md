```
coeff(x::FqFieldElem, n::Int) -> FqFieldElem
```

Given an element $x$ of a finite field $K$, return the degree $n$ coefficient (as an element of the base field) of $x$ when expressed in the power basis of $K$.

# Examples

```jldoctest
julia> K, a = finite_field(9, "a");

julia> x = 2 * a + 1
2*a + 1

julia> coeff(x, 1)
2

julia> x == sum([coeff(x, i - 1) * basis(K)[i] for i in 1:degree(K)]) ==
            sum([coeff(x, i) * a^i for i in 0:degree(K) - 1])
true
```
