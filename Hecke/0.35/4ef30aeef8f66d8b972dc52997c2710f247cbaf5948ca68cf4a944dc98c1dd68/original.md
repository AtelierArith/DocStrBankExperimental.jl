```
cyclotomic_polynomial(n::Int, R::PolyRing{T} = Hecke.Globals.Zx) where T
                                                              -> PolyRingElem{T}
```

Return the `n`-th cyclotomic polynomial as an element of `R`. If `R` is not specified, return the `n`-th cyclotomic polynomial over the integers.

# Examples

```jldoctest
julia> F, _ = finite_field(5)
(Prime field of characteristic 5, 0)

julia> Ft, _ = F["t"]
(Univariate polynomial ring in t over F, t)

julia> cyclotomic_polynomial(15, Ft)
t^8 + 4*t^7 + t^5 + 4*t^4 + t^3 + 4*t + 1

julia> cyclotomic_polynomial(9)
x^6 + x^3 + 1

julia> typeof(ans)
ZZPolyRingElem
```
