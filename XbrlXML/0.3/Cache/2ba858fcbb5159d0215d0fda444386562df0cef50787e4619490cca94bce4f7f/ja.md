```
header!(cache::HttpCache, header::Pair)::Dict
```

キャッシュにヘッダーペアを追加し、ヘッダーを返します。

# 例

```jldoctest
julia> using XbrlXML

julia> cache = HttpCache("/Users/user/cache/");

julia> header!(cache, "User-Agent" => "You youremail@domain.com")
Dict{String, String} with 1 entry:
  "User-Agent" => "You youremail@domain.com"
```
