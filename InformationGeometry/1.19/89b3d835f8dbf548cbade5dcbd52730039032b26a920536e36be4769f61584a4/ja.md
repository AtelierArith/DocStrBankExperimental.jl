```
BiExp(y::Union{T, AbstractVector{T}}; C::Real=one(T)) where T<:Number
```

双対対称指数を計算します。これは[`BiLog`](@ref)への逆変換です。

$$
BiExp(y) = \sgn(y) \cdot 1/C \cdot (\exp(|y|) - 1)
$$

https://doi.org/10.1088/0957-0233/24/2/027001の定義に似ています。定数`C`はゼロでの双対対数の傾きを制御します。すなわち、双対指数は傾き`1/C`を持ちます。
