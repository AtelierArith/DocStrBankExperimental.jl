```
NLLSsolver.storecostscallback(store)
```

イテレーションごとの情報を `store` に保存するコールバックを生成します。

# 例

次のようにNLLSsolver問題を最適化します：

```julia
    costs = Vector{Float64}()
    NLLSsolver.optimize!(problem, options, unfixed, storecostscallback(costs))
```

これにより、各イテレーションの終了時にコストがベクトル `costs` に保存されます。一方：

```julia
    costtrajectory = CostTrajectory()
    NLLSsolver.optimize!(problem, options, unfixed, storecostscallback(costtrajectory))
```

これにより、各イテレーションの終了時にコスト、ステップ、および最適化時間が [`CostTrajectory`](@ref) 構造体に保存されます。

!!! note
    このメソッドはデバッグに役立ちますが、パフォーマンスにペナルティが発生します。

