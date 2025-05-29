```
Floatmu{szE,szf} <: AbstractFloat
```

IEEE 754準拠の浮動小数点数で、`szE`ビットの指数部と`szf`ビットの小数部を持ちます。

`Floatmu`オブジェクトは常に単精度浮動小数点数の精度以下でなければなりません。その結果、以下の制約が成り立ちます：

$$
\left\{\begin{array}{l}
\text{szE}\in[2,8]\\
\text{szf}\in[2,23]
\end{array}\right.
$$

# 例

`Float32`に相当する`Floatmu`型の作成：

```jldoctest
julia> MyFloat32 = Floatmu{8,23}
Floatmu{8, 23}

julia> a=MyFloat32(0.1)
0.1

julia> a == 0.1f0
true
```
