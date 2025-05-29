```
x(mod::Model)
```

モデルパラメータの*変数*を返します。これは`mod.x_ind`で指定された順序に従います。

## デフォルト

  * `mod.val[mod.x_ind]::Vector{Float64}`を返します。
