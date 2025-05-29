```
`unconstrained_check( :: AbstractNLPModel, :: NLPAtX; pnorm :: Real = Inf, kwargs...)`
```

目的関数の勾配の `pnorm`-ノルムを返します。

`state.gx` が必要です（提供されていない場合は埋める必要があります）。

関連情報として `optim_check_bounded`, `KKT` を参照してください。
