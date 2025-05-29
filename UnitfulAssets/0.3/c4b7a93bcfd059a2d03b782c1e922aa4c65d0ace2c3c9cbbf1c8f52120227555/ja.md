```
generate_exchmkt(a::Array{Pair{Tuple{String,String},Float64},1})
```

単一のベース-クォート-バリュー レートから `ExchangeMarket` のインスタンスを生成します。

# 例

```jldoctest
julia> generate_exchmkt(("EUR", "USD") => 1.164151)
Dict{AssetsPair,Float64} with 1 entry:
  AssetsPair("EUR", "USD") => Rate(1.16415)
```
