```
freeze!(@nospecialize(ids::T)) where {T<:Union{IDS,IDSvector}}
```

すべての式をその場で評価します

注意: 失敗した式は `missing` になります
