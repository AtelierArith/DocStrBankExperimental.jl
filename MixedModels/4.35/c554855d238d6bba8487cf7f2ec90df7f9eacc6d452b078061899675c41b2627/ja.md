```
refit!(m::LinearMixedModel[, y::Vector]; REML=m.optsum.REML, kwargs...)
```

応答 `y` をインストールした後にモデル `m` を再適合させます。

`y` が省略された場合、現在の応答ベクトルが使用されます。`kwargs` は [`fit!`](@ref) と同じです。
