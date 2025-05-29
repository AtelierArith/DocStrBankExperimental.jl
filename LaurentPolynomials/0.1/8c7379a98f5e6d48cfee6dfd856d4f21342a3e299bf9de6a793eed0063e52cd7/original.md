`pseudodiv(a::Pol, b::Pol)`

pseudo-division  of `a` by `b`.  If `d` is the  leading coefficient of `b`, computes   `(q,r)`   such   that   `d^(degree(a)+1-degree(b))a=q*b+r`   and `degree(r)<degree(b)`. Does not do division so works over any ring. For true polynomials (errors if the valuation of `a` or of `b` is negative).

```julia-repl
julia> pseudodiv(q^2+1,2q+1)
(2q-1, 5)

julia> (2q+1)*(2q-1)+5
Pol{Int64}: 4q²+4
```

See Knuth AOCP2 4.6.1 Algorithm R
