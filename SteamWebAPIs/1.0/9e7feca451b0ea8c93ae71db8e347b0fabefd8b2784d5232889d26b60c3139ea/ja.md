```
get_countries()::Dict{String,Tuple{Bool,String}}
```

**概要**: `get_countries` は国の Dict を返します。キーは国コード、値はタプルで、タプルの最初の要素は州があるかどうかを示し、2 番目は国名です。

# 例

```julia-repl
julia> get_countries()
countries = Dict("ES" => (1, "Spain")...)
```
