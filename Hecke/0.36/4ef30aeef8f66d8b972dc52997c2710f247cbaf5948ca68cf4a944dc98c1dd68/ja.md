```
cyclotomic_polynomial(n::Int, R::PolyRing{T} = Hecke.Globals.Zx) where T
                                                              -> PolyRingElem{T}
```

`n`-番目のサイクロトミック多項式を `R` の要素として返します。`R` が指定されていない場合は、整数上の `n`-番目のサイクロトミック多項式を返します。

# 例

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
