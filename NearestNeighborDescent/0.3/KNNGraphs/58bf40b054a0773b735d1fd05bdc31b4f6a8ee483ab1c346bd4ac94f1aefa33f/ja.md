ApproximateKNNGraph{V, U, D, M} サブタイプは、各頂点が重みの型 `U` を持つちょうど `k` 本の前方エッジを持つ重み付き有向グラフです。

`D` はこのグラフに対応するデータセットの型であり、`M` は結果の型が `U` に一致する `Distances.PreMetric` です。
