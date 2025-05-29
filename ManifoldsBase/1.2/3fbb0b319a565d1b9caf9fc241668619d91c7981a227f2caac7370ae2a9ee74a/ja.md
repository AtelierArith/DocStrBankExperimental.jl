```
SoftmaxInverseRetraction <: AbstractInverseRetractionMethod
```

ソフトマックス関数に基づく逆リトラクションを説明します。

!!! note "技術的注意"
    逆ソフトマックスリトラクションを実装するには、例えば [`inverse_retract`](@ref)`(M, p, q, SoftmaxInverseRetraction())` と呼び出すことになりますが、あなたの多様体 `M` に対して [`inverse_retract_softmax!`](@ref)`(M, X, p, q)` を定義してください。

