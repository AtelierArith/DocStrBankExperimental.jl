```
branchlength_update!(bl_modifier::UnivariateModifier, tree::FelNode, models; <キーワード引数>)
```

[`branchlength_optim!`](@ref) のより一般的なバージョンです。ここで `bl_modifier` はオプティマイザーまたはサンプラー（またはより一般的には UnivariateModifier）であることができます。

# キーワード引数

[`branchlength_optim!`](@ref) を参照してください。

!!! note
    `bl_modifier` はここでは位置引数であり、キーワード引数ではありません。

