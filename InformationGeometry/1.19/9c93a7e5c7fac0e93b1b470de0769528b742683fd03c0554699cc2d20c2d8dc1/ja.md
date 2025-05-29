```
BiLog(x::Union{T, AbstractVector{T}}; C::Real=one(T)) where T<:Number
```

バイ対称対数を計算します。これは負の数にも適用できます。

$$
BiLog(x) = \sgn(x) \sgn(C) \cdot \log(1 + |C| \cdot |x|)
$$

https://doi.org/10.1088/0957-0233/24/2/027001 の定義に似ています。定数 `C` はゼロでのバイ対数の傾きを制御します。逆変換は [`BiExp`](@ref) で与えられます。
