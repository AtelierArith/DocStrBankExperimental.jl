```
integral_split(a::FieldElem, O::Ring)
```

For an element of the quotient field of some ring $O$, decompose $a$ as an element $n$ in $O$ and some denominator $d$, either in $O$ or the coefficient ring of $O$.

# EXAMPLES

```julia
julia> integral_split(1//3, ZZ)
(1, 3)

julia> k, a = quadratic_field(5);

julia> zk = maximal_order(k);

julia> integral_split(1//a, zk)
(5, [-1 2])
```
