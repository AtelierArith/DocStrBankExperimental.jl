```julia
Flow(prob, alg; kwargs...)

```

`prob::ODEProblem` と ODE ソルバー `alg` に基づいて `Flow` 変数を作成します。ベクトル場 `F` を渡す必要がありますが、これは将来的に解決される予定で、`prob` から復元できます。また、フローの導関数は有限差分で推定されます。
