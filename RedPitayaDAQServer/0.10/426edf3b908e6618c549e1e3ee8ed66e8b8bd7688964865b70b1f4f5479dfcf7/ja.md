```
samplesPerPeriod!(rp::RedPitaya, value)
```

周期あたりのサンプル数を設定します。

# 例

```julia
julia> samplesPerPeriod!(rp, 256)
true

julia> samplesPerPeriod(rp)
256

```
