```
`KKT( :: AbstractNLPModel, :: NLPAtX; pnorm :: Real = Inf, kwargs...)`
```

KKT条件を確認します。

注意: `state.gx` は必須です + 制約 `state.mu` がある場合 + 制約 `state.cx`, `state.Jx`, `state.lambda` がある場合。

また、`unconstrained_check`、`optim_check_bounded` も参照してください。
