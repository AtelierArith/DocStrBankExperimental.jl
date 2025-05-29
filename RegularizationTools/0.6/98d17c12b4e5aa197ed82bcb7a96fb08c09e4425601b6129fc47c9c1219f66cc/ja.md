```
gcv_svd(Ψ::RegularizationProblem, b̄::AbstractVector, λ::AbstractFloat)
```

トレース項を使用してSVDアルゴリズムを用いた[一般化交差検証](@ref)を計算します。ベクトルb̄が標準形である必要があります。

使用例

```julia
using Underscores

Ψ = setupRegularizationProblem(A, 1)            # 問題を設定
b̄, x̄₀ = to_standard_form(Ψ, b, x₀)              # 標準形に変換
Vλ = gcv_svd(Ψ, b̄, x̄₀, 0.1)                     # V(λ) 単一のλ値
Vλ = @_ map(gcv_svd(Ψ, b̄, _), [0.1, 1.0, 10.0]) # V(λ) λの配列に対して
```
