```
BiPower(y::Union{T, AbstractVector{T}}, m::Real=2.0; C::Real=one(T)) where T<:Number
```

双対対称 `m`-乗を計算します。これは、[`BiRoot`](@ref) の逆変換であり、[`BiPower`](@ref) の傾きが原点で `1/C` になるようにします（すなわち、元の [`BiRoot`](@ref) の傾きは `C` です）：

$$
BiPower_m(y) = \sgn(x) \cdot (m C)^{-1} \cdot ((1 + |y|)^m - 1)
$$

双対対称の根と乗は、https://doi.org/10.1088/0957-0233/24/2/027001 の双対対称対数に触発されています。
