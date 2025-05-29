```
trace_of_frobenius(E::EllipticCurve{<: FinFieldElem}, r::Int) -> ZZRingElem
```

楕円曲線 $E$ に対するフロベニウス自己同型の $r$ 乗のトレースを返します。

```jldoctest
julia> E = elliptic_curve(GF(101, 2), [1, 2]);

julia> trace_of_frobenius(E, 2)
18802
```
