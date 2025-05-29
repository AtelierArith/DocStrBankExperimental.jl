```
unitknot
```

ユニットノットは空のタプルを保持します。

```jldoctest
julia> unitknot
┼──┼
│  │
```

`unitknot`は、他のデータソースから発生しないクエリを構築するのに便利です。

```jldoctest
julia> unitknot["Hello"]
┼───────┼
│ Hello │
```
