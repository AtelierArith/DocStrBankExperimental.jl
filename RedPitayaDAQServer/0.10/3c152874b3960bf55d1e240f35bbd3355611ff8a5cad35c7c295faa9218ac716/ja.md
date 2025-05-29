```
samplesPerPeriod(rp::RedPitaya)
```

周期あたりのサンプル数を返します。

# 例

```julia
julia> samplesPerPeriod!(rp, 256)
true

julia> samplesPerPeriod(rp)
256

```
