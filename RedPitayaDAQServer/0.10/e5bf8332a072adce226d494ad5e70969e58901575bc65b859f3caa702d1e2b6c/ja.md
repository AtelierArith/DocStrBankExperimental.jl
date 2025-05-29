```
counterTrigger_arm!(rp::RedPitaya, val::Bool)
```

カウンタートリガーがアームされているかどうかを設定します。コマンドが成功した場合は `true` を返します。

# 例

```julia
julia> counterTrigger_arm!(rp, true)
true

julia> counterTrigger_isArmed(rp)
true
```
