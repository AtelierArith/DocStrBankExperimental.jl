```
quadreg(μ, ν, C, ε, alg::QuadraticOT; kwargs...)
```

ヒストグラム `μ` と `ν` の最適輸送計画を、コスト行列 `C` と二次正則化パラメータ `ε` を用いて計算します。

最適輸送計画 `γ` は `C` と同じサイズであり、次の問題を解きます。

$$
\inf_{\gamma \in \Pi(\mu, \nu)} \langle \gamma, C \rangle
+ \varepsilon \Omega(\gamma),
$$

ここで、$\Omega(\gamma) = \frac{1}{2} \sum_{i,j} \gamma_{i,j}^2$ は二次正則化項です。

`check_convergence` の各ステップで、輸送計画 `γ` の反復が次の条件を満たすかどうかを確認することで、アルゴリズムが収束しているかどうかが評価されます。

```julia
    norm_diff < max(atol, rtol * max(norm(μ, Inf), norm(ν, Inf)))
```

ここで、

$$
    \text{normdiff} = \max\{ \| \gamma \mathbf{1} - \mu \|_\infty , \|  \gamma^\top \mathbf{1} - \nu \|_\infty  \} . 
$$

`maxiter` 回の反復後、計算は停止します。

エントロピー正則化のためのSinkhornアルゴリズムの場合とは異なり、二次正則化のための最適輸送のバッチ計算はサポートされていないことに注意してください。

関連情報: [`sinkhorn`](@ref), [`QuadraticOTNewton`](@ref)
