```
path(::AirBase)
```

APIパスへのアクセサ関数です。これは、APIバージョン番号（現時点では`v0`のみ）に続くベースIDです。

```jldoctest
julia> b = AirBase("appphImnhJO8AXmmo");

julia> path(b)
"/v0/appphImnhJO8AXmmo"
```
