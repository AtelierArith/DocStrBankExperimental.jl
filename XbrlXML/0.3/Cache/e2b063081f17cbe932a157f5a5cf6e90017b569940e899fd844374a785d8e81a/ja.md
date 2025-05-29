```
cachedir(cache::HttpCache)::String
```

キャッシュのローカルディレクトリを返します。

# 例

```jldoctest
julia> using XbrlXML

julia> cache = HttpCache("/Users/user/cache/");

julia> cachedir(cache)
"/Users/user/cache/"
```
