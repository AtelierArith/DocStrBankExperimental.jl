```
QRRetraction <: AbstractRetractionMethod
```

行列 / 行列の QR 分解に基づく再収束で、点と接ベクトルに対して [`AbstractManifold`](@ref) を使用します。

!!! note "技術的注意"
    例えば [`retract`](@ref)`(M, p, X, QRRetraction())` と呼び出して QR 再収束を実装することになりますが、あなたの多様体 `M` のために [`retract_qr!`](@ref)`(M, q, p, X, t)` を定義してください。

