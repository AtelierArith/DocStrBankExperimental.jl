```
get_movers(idx_symbol::T,
           dire::T="up",
           chg::T="percent") where T<:AbstractString
```

インデックスの上位10件（上昇または下降）を取得します: https://developer.tdameritrade.com/movers/apis/get/marketdata/{index}/movers

# 引数

dire = "up" または "down" chg = "value" または "percent"

# 例

```julia
get_movers(raw"$DJI")
get_movers("$DJI", "up", "value")
```
