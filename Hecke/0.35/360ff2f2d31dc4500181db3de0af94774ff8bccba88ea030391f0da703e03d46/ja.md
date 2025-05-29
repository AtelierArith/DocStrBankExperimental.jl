```
trace_of_frobenius(E::EllipticCurve{FinFieldElem}) -> Int
```

楕円曲線 $E$ のフロベニウス自己同型のトレースを返します。これは $n$ が $\mathbf{F}_q$ 上の $E$ の点の数であるとき、$q + 1 - n$ に等しいです。

# 例

```jldoctest
julia> E = elliptic_curve(GF(101), [1, 2]);

julia> trace_of_frobenius(E) == 101 + 1 - order(E)
true
```
