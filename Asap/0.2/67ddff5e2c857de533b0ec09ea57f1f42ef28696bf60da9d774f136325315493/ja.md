```
FDMelement(points::Vector{FDMnode}, iStart::Int64, iEnd::Int64, q::Real, id = :element)
FDMelement(points::Vector{FDMnode}, indices::Vector{Int64}, q::Real, id = :element)
FDMelement(pointStart::FDMnode, pointEnd::FDMnode, q::Real, id = :element)
```

力密度法ネットワークにおける要素で、2つのノードを力密度 `q` で接続し、オプションの識別子 `id::Symbol` を持ちます。
