```
save_graphml(graphml_file::String, eng::Dict{String,<:Any}; type::String="nested")
```

`eng`ネットワークデータから構築されたGraphML XMLドキュメントを`graphml_file`に保存します。

`type`は、結果のグラフがネストされたグラフ（すなわち、バスが負荷ブロック内に含まれる）であるか、非ネストされたグラフ（ノードグループが利用されない）であるかを制御します。
