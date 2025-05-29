```
`optim_check_bounded( :: AbstractNLPModel, :: NLPAtX; pnorm :: Real = Inf, kwargs...)`
```

目的関数の勾配の `pnorm`-ノルムを境界に投影してチェックします。

`state.gx` が必要です（提供されていない場合は埋める必要があります）。

関連情報として `unconstrained_check`、`KKT` を参照してください。
