```
gcv_tr(Ψ::RegularizationProblem, b̄::AbstractVector, λ::AbstractFloat)
```

トレース項を使用して[一般化交差検証](@ref)を計算します。ベクトルb̄が標準形式である必要があります。

$$
V(\lambda)=\frac{n\left\lVert ({\bf {\rm {\bf {\bf I}-}{\bf \bar {A}_{\lambda}})
{\bar{\rm b}}}}\right\rVert _{2}^{2}}{tr({\rm {\bf I}-{\rm {\bar {\bf A}_{\lambda}})}^{2}}}
$$

使用例

```julia
using Underscores

Ψ = setupRegularizationProblem(A, 1)           # 問題を設定
b̄ = to_standard_form(Ψ, b)                     # 標準形式に変換
Vλ = gcv_tr(Ψ, b̄, 0.1)                         # V(λ) 単一のλ値
Vλ = @_ map(gcv_tr(Ψ, b̄, _), [0.1, 1.0, 10.0]) # V(λ) λの配列に対して
```
