```julia
struct BoundedLinear{T<:Real} <: SpectralKit.AbstractUnivariateTransformation
```

ドメインを `y ∈ (a, b)` に変換します。$y = x ⋅ s + m$ を使用します。

`m` と `s` はコンストラクタによって計算され、チェックされます；`a < b` が強制されます。
