```
BiRoot(x::Union{T, AbstractVector{T}}, m::Real=2.0; C::Real=one(T)) where T<:Number
```

双対対称 `m`-乗根を計算します。これは、原点での傾きが `C` となるように [`BiPower`](@ref) の逆変換です：

$$
BiRoot_m(x) = \sgn(x) \sgn(C) \cdot ((1 + m \cdot |C| \cdot |x|)^{1/m} -1)
$$

双対対称の根と累乗は、https://doi.org/10.1088/0957-0233/24/2/027001 の双対対称対数に触発されています。
