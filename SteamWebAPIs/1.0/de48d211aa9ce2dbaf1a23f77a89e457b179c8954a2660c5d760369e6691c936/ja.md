```
get_cities(countrycode::String,statecode::String)::Dict{Int,String}
```

**概要**: `get_cities` は、国コードと州コードによって都市の辞書を返します。キーは都市コード、値は都市名です。

# 引数

  * `countrycode`: 照会する国コード。
  * `statecode`: 照会する州コード。

# 例

```julia-repl
julia> get_cities("CN","01")
cites = Dict(10398 => "Wucheng"...)
```
