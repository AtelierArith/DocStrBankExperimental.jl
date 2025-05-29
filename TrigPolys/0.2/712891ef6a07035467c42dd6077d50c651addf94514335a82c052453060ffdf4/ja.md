```
struct TrigPoly{T<:AbstractFloat, VT<:AbstractVector{T}}
    a0::T    # 定数係数
    ac::VT   # cos 係数
    as::VT   # sin 係数
end
```

係数によって *エルミート三角多項式* を表します。ベクトル `ac` と `as` は同じ長さである必要があり、このドキュメントではそれを `n` と呼びます。これは次の関数を表します。

```julia
R(ω) = a0 + sum(ac[k] * cos(k * ω) + as[k] * sin(k * ω) for k in 1:n)
```

これは変数 `x = cos(ω)` に関する多項式です。
