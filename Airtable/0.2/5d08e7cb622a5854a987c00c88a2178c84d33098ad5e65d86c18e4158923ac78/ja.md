```
path(::AirTable)
```

テーブルへのAPIパスのアクセサ関数です。これは、[ベースへのパス](@ref `path(::AirBase)`)の前にテーブルIDが付いたものです。

```jldoctest
julia> b = AirBase("appphImnhJO8AXmmo");

julia> tab = AirTable("Table 1", b);

julia> path(tab)
"/v0/appphImnhJO8AXmmo/Table 1"
```
