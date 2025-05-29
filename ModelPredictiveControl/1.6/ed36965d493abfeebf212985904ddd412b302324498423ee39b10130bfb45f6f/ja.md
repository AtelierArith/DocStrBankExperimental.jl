```
ExplicitMPC(estim::StateEstimator; <keyword arguments>)
```

カスタム状態推定器 `estim` を使用して `ExplicitMPC` を構築します。

`estim.model` は [`LinModel`](@ref) でなければなりません。そうでない場合は、[`NonLinMPC`](@ref) が必要です。
