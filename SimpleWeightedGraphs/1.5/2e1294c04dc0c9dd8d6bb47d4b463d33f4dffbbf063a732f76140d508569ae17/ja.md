```
SimpleWeightedGraph{T, U}
```

`T`型の頂点と`U`型のエッジ重みを持つ無向重み付きグラフを表す型です。

# フィールド

  * `weights::SparseMatrixCSC{U,T}`: 重み付き隣接行列、`(dst, src)`でインデックス付けされています。

!!! tip "パフォーマンス"
    このタイプのグラフでは、頂点やエッジを反復的に追加/削除することはあまり効率的ではありません。可能であれば、一度にグラフを構築する方が良いです。


# 基本コンストラクタ

```
SimpleWeightedGraph()  # 空
SimpleWeightedGraph(n)  # n 頂点、エッジなし
SimpleWeightedGraph(graph)  # グラフから
SimpleWeightedGraph(adjmx)  # 隣接行列から
SimpleWeightedGraph(sources, destinations, weights)  # エッジのリストから
```

完全なコンストラクタのリストについては`methods(SimpleWeightedGraph)`を使用してください。エッジのリストから新しいグラフを構築する際は、`(src, dst)`ペアを繰り返すと未定義の動作を引き起こす可能性があることに注意してください（例：重みの加算中の浮動小数点エラーによる）。
