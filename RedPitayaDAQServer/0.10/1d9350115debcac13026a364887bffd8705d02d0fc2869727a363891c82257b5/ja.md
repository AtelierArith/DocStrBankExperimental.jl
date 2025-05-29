```
counterTrigger_enabled(rp::RedPitaya)
```

カウンタートリガーが有効かどうかを返します。

# 例

```julia
julia> counterTrigger_enabled!(rp, true)
true

julia> counterTrigger_enabled(rp)
true
```
