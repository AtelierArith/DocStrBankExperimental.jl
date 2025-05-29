```
QRInverseRetraction <: AbstractInverseRetractionMethod
```

行列 / 行列の QR 分解に基づく逆再収束で、点と接ベクトルに対して [`AbstractManifold`](@ref) 上で定義されます。

!!! note "技術的注意"
    逆 QR 再収束を実装するために、例えば [`inverse_retract`](@ref)`(M, p, q, QRInverseRetraction())` と呼び出すことになりますが、あなたの多様体 `M` に対して [`inverse_retract_qr!`](@ref)`(M, X, p, q)` を定義してください。

