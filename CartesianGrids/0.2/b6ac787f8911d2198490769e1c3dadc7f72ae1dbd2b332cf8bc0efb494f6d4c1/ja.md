gridwise_dot(u::Edges{Primal/Dual},v::Edges{Primal/Dual})

ベクトルグリッドデータ `u` と `v` のドット積を計算し、結果をセルの中心（データが Edges{Primal} の場合）またはノード（データが Edges{Dual} の場合）に配置します。
