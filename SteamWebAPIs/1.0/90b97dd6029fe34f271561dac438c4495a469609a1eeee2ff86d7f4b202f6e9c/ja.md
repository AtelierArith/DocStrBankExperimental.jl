```
get_states(countrycode::String)::Dict{String,String}
```

**概要**: `get_states` は、国コードによる州の辞書を返します。キーは州コード、値は州名です。

# 引数

  * `countrycode`: 照会する国コード。

# 例

```julia-repl
julia> get_states("CN")
Dict("24" => "Shanxi"...)
```
