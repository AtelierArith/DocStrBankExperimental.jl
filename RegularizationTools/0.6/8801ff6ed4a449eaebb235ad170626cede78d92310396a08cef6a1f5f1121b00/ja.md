```
solve(Ψ::RegularizationProblem, b̄::AbstractVector, x̄₀::AbstractVector, λ::AbstractFloat)
```

問題 Ψ のティホノフ解を正則化パラメータ λ に対して標準形式で計算し、x̄₀ を初期推定値として使用します。

$$
{\rm x_{\lambda}}=\left({\rm {\bf \bar A}^{T}}{\rm {\bf \bar A}}+\lambda^{2}{\rm {\bf I}}\right)^{-1} 
\left({\rm {\bf {\bar A}}^{T}}{\rm {\bar b}} + \lambda^2 {\rm {\bar x}}_0 \right)
$$

使用例（標準構文）

```julia
# A は行列で、b は応答ベクトルです。 
Ψ = setupRegularizationProblem(A, 2)     # 問題を設定
b̄, x̄₀ = to_standard_form(Ψ, b, x₀)       # 標準形式に変換
x̄ = solve(A, b̄, x̄₀, 0.5)                 # 方程式を解く
x = to_general_form(Ψ, b, x̄)             # 一般形式に戻す
```
