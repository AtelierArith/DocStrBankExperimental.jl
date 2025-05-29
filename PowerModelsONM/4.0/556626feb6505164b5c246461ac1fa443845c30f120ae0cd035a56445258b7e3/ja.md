```
build_graphml_document(eng::Dict{String,<:Any}; type::Type="nested")
```

`eng` ネットワークデータ構造から GraphML XML ドキュメントを構築するためのヘルパー関数です。

`type` は、結果のグラフが NestedGraph であるか、すなわちバスが負荷ブロック内に含まれるか、または UnnestedGraph であるかを制御します。ノードグループは利用されません。
