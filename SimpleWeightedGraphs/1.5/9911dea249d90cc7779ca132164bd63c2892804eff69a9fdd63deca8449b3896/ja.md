```
SimpleWeightedDiGraph{T,U}
```

型 `T` の頂点と型 `U` の辺の重みを持つ有向重み付きグラフを表す型です。

# フィールド

  * `weights::SparseMatrixCSC{U,T}`: 重み付き隣接行列、`(dst, src)` でインデックス付けされています。

!!! tip "パフォーマンス"
    このタイプのグラフでは、頂点や辺を反復的に追加/削除することはあまり効率的ではありません: 可能であれば、一度にグラフを構築する方が良いです。


# 基本コンストラクタ

```
SimpleWeightedDiGraph()  # 空
SimpleWeightedDiGraph(n)  # n 頂点、辺なし
SimpleWeightedDiGraph(graph)  # グラフから
SimpleWeightedDiGraph(adjmx; permute)  # 隣接行列から、転置されている可能性あり
SimpleWeightedDiGraph(sources, destinations, weights)  # 辺のリストから
```

完全なコンストラクタのリストについては `methods(SimpleWeightedDiGraph)` を使用してください。辺のリストから新しいグラフを構築する際は、`(src, dst)` ペアを繰り返すと未定義の動作を引き起こす可能性があることに注意してください（例: 重みの加算中の浮動小数点エラーによる）。
