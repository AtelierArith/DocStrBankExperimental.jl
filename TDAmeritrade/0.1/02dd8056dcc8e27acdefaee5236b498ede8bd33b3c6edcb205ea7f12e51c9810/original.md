```
get_movers(idx_symbol::T,
           dire::T="up",
           chg::T="percent") where T<:AbstractString
```

Get top 10 (up or down) movers of an idx: https://developer.tdameritrade.com/movers/apis/get/marketdata/{index}/movers

# Arguments

dire = "up" or "down" chg = "value" or "percent"

# Examples

```julia
get_movers(raw"$DJI")
get_movers("$DJI", "up", "value")
```
