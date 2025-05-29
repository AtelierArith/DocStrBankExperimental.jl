```
lambertw(z::Complex{T}, k::V=0) where {T<:Real, V<:Integer}
lambertw(z::T, k::V=0) where {T<:Real, V<:Integer}
```

`z`の`k`番目の分岐のランベルトW関数を計算します。`z`が実数の場合、`k`は`0`または`-1`のいずれかでなければなりません。実数`z`の場合、分岐`k = -1`の定義域は`[-1/e, 0]`であり、分岐`k = 0`の定義域は`[-1/e, Inf]`です。複素数`z`の場合、すべての`k`に対して定義域は複素平面です。

```jldoctest
julia> lambertw(-1/e, -1)
-1.0

julia> lambertw(-1/e, 0)
-1.0

julia> lambertw(0, 0)
0.0

julia> lambertw(0, -1)
-Inf

julia> lambertw(Complex(-10.0, 3.0), 4)
-0.9274337508660128 + 26.37693445371142im
```
