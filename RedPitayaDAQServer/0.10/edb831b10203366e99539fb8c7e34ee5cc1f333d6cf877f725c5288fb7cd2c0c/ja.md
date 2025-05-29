```
counterTrigger_reset(rp::RedPitaya)
```

カウンタートリガーのリセット状態を返します。

# 例

```julia
julia> counterTrigger_reset!(rp, true)

julia>counterTrigger_reset(rp)
true
```
