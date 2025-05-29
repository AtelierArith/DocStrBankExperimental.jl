```
par(mod::Model)
```

`mod.par_ind`で指定された順序に従って、*固定*モデルパラメータを返します。

## デフォルト

  * `mod.val[mod.par_ind]::Vector{Float64}`を返します。
