```
HttpCache(cache_dir="./cache/", headers=Dict())
```

ローカルにファイルを再利用するためのキャッシュを作成します。

`headers` は http `Downloads.download` に渡されます。SEC などのサービスでは、アプリケーションに関する情報を開示する必要があります。

# 例

```jldoctest
julia> using XbrlXML

julia> cache = HttpCache("/Users/user/cache/")
/Users/user/cache/
```
