```
ShiftNet
```

ツリーのノードにマッピングされたシフトと、それらの（ユニークな）親エッジが [`PhyloNetworks.HybridNetwork`](@extref) においてトポロジカル順にソートされています。その `shift` フィールドは、各ノードに対するシフト値のベクトルであり、ノードの親エッジ上のシフトに対応しています（これはツリーノードにのみ意味があります：それらは単一の親エッジを持ちます）。

同じネットワーク上の2つの `ShiftNet` オブジェクトは `*` で連結できます。

`ShiftNet(node::Vector{Node}, value::AbstractVector, net::HybridNetwork; checkpreorder::Bool=true)`

ノードのベクトルと関連する値からのコンストラクタです。シフトは提供されたノードの上のエッジに位置しています。警告、ハイブリッドエッジ上のシフトは許可されていません。

`ShiftNet(edge::Vector{Edge}, value::AbstractVector, net::HybridNetwork; checkpreorder::Bool=true)`

エッジのベクトルと関連する値からのコンストラクタです。警告、ハイブリッドエッジ上のシフトは許可されていません。

エクストラクタ: [`getshiftedgenumber`](@ref), [`getshiftvalue`](@ref)
