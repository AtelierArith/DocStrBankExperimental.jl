```
FunctionVectorialType{P<:AbstractPowerRepresentation} <: AbstractVectorialType
```

制約が全体の関数に実装されていることを示す型、例えば $g(p) ∈ ℝ^m$ または $\operatorname{grad} g(p) ∈ (T_p\mathcal M)^m$。

この型は、特にヘッセ行列や勾配関数に関して意味がある場合に、内部的に [`AbstractPowerRepresentation`](@extref `ManifoldsBase.AbstractPowerRepresentation`) を格納します。
