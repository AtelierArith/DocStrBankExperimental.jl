```
slowDACClockDivider!(rp::RedPitaya, val::Int32)
```

スローダックのクロック分周器を設定します。

# 例

```julia
julia> slowDACClockDivider!(rp, 8)

julia>slowDACClockDivider(rp)
8
```
