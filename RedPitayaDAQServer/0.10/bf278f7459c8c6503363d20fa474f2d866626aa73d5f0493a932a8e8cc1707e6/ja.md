counterTrigger_enabled!(rp::RedPitaya, val)

カウンタートリガーが有効かどうかを設定します。コマンドが成功した場合は `true` を返します。

# 例

```julia
julia> counterTrigger_enabled!(rp, true)
true

julia> counterTrigger_enabled(rp)
true
```
