```
gcv_tr(
    Ψ::RegularizationProblem,
    b̄::AbstractVector,
    x̄₀::AbstractVector,
    λ::AbstractFloat,
)
```

トレース項と初期推定を使用して[一般化交差検証](@ref)を計算します。ベクトルb̄とx̄₀は標準形である必要があります。

$$
V(\lambda)=\frac{n\left\lVert {\bf {\rm {\bf \bar{A}}{\rm \bar{x}{}_{\lambda}}-
{\rm \bar{b}}}}\right\rVert _{2}^{2}}{tr({\rm {\bf I}-{\rm {\bar {\bf A}_{\lambda}})}^{2}}}
$$

使用例

```julia
using Underscores

Ψ = setupRegularizationProblem(A, 1)               # 問題を設定
b̄, x̄₀ = to_standard_form(Ψ, b, x₀)                 # 標準形に変換
Vλ = gcv_tr(Ψ, b̄, x̄₀, 0.1)                         # V(λ) 単一のλ値
Vλ = @_ map(gcv_tr(Ψ, b̄, x̄₀, _), [0.1, 1.0, 10.0]) # V(λ) λの配列
```
