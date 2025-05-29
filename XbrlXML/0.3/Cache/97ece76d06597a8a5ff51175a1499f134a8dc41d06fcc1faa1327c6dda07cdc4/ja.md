```
headers(cache::HttpCache)::Dict
```

キャッシュのヘッダーを返します。

# 例

```jldoctest
julia> using XbrlXML

julia> cache = HttpCache("/Users/user/cache/");

julia> header!(cache, "User-Agent" => "You youremail@domain.com");

julia> headers(cache)
Dict{String, String} with 1 entry:
  "User-Agent" => "You youremail@domain.com"
```
