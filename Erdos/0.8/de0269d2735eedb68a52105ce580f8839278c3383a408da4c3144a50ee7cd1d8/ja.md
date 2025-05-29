```
mutable struct PropertyStore
    gmaps::Dict{String, Any}
    emaps::Dict{String,AEdgeMap}
    vmaps::Dict{String,AVertexMap}
end
```

ネットワークに関連付けられたプロパティを格納する型です。
