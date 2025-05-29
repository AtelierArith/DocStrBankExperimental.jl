```
SoftmaxRetraction <: AbstractRetractionMethod
```

ソフトマックス関数に基づくリトラクションを説明します。

!!! note "技術的注意"
    ソフトマックスリトラクションを実装するために、例えば [`retract`](@ref)`(M, p, X, SoftmaxRetraction())` と呼び出すことになりますが、あなたの多様体 `M` に対して [`retract_softmax!`](@ref)`(M, q, p, X, t)` を定義してください。

