```
counterTrigger_reset!(rp::RedPitaya, val::Bool)
```

カウンタートリガーのリセットを `val` に設定します。コマンドが成功した場合は `true` を返します。

# 例

```julia
julia> counterTrigger_reset!(rp, true)
true

julia>counterTrigger_reset(rp)
true
```
