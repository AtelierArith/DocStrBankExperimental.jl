```
save_graphml(io::IO, eng::Dict{String,<:Any}; type::String="nested")
```

`eng` ネットワークデータから構築された GraphML XML ドキュメントを IO ストリームに保存します。

`type` は、結果のグラフが NestedGraph であるかどうかを制御します。つまり、バスが負荷ブロック内に含まれるか、ノードグループが利用されない UnnestedGraph であるかを制御します。
