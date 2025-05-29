```
rand(::Unitary; vector_at=nothing, σ::Real=1.0)
```

[`UnitaryMatrices`](@ref) マニフォールド上のランダムな点を生成します。`vector_at` が nothing の場合、$n×x$ 行列の QR 分解を計算します。

`vector_at` で接ベクトルを生成するには、通常分布に従う行列を接空間に射影します。
