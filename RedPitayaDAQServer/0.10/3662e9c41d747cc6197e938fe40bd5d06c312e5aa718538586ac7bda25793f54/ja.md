```
counterTrigger_isArmed(rp::RedPitaya)
```

カウンタートリガーがアームされているかどうかを返します。

# 例

```julia
julia> counterTrigger_arm!(rp, true)
true

julia> counterTrigger_isArmed(rp)
true
```
