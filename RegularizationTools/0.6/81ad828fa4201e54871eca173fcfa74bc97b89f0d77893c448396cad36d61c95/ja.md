```
solve(Ψ::RegularizationProblem, b̄::AbstractVector, λ::AbstractFloat)
```

問題 Ψ のティホノフ解を正則化パラメータ λ に対して、初期推定値をゼロとして標準形式で計算します。ベクトル $\rm {\bar x}_\lambda$ を返します。

$$
{\rm x_{\lambda}}=\left({\rm {\bf \bar A}^{T}}{\rm {\bf \bar A}}+\lambda^{2}{\rm {\bf I}}\right)^{-1} 
{\rm {\bf {\bar A}}^{T}}{\rm {\bar b}} 
$$

使用例 (標準構文)

```julia
# A は行列で、b は応答ベクトルです。 
Ψ = setupRegularizationProblem(A, 1)     # 問題を設定
b̄ = to_standard_form(Ψ, b)               # 標準形式に変換
x̄ = solve(A, b̄, 0.5)                     # 方程式を解く
x = to_general_form(Ψ, b, x̄)             # 一般形式に戻す
```

使用例 (遅延構文)

```julia
# A は行列で、b は応答ベクトルです。 
Ψ = setupRegularizationProblem(A, 1)     # 問題を設定
b̄ = @>> b to_standard_form(Ψ)            # 標準形式に変換
x̄ = solve(A, b̄, 0.5)                     # 方程式を解く
x = @>> x̄ to_general_form(Ψ, b)          # 一般形式に戻す
```
