```
find_corresponding_dim_name(dim_name::AbstractString, dim_names::Iterable)
```

`dim_names`の中で`dim_name`に一致する対応する次元名を見つけます。

次元の2つの名前が一致するのは、両方が`Var.conventional_dim_name`によって決定される同じ従来の名前に対応する場合です。

# 例

```jldoctest
julia> ClimaAnalysis.Var.find_corresponding_dim_name("longitude", ["lat", "lon"])
"lon"

julia> ClimaAnalysis.Var.find_corresponding_dim_name("time", ["lat", "lon", "t"])
"t"

julia> ClimaAnalysis.Var.find_corresponding_dim_name("height", ["lat", "lon", "height"])
"height"
```
