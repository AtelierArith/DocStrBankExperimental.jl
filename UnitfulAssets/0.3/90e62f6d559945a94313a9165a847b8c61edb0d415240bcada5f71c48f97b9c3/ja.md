```
generate_exchmkt(d::Dict{Tuple{String,String},T}) where {T<:Number}
```

ベース-クォート-バリュー レートの辞書から `ExchangeMarket` のインスタンスを生成します。

# 例

```jldoctest
julia> generate_exchmkt(Dict(("EUR", "USD") => 1.164151))
Dict{AssetsPair,Float64} with 1 entry:
  AssetsPair("EUR", "USD") => Rate(1.16415)
```
