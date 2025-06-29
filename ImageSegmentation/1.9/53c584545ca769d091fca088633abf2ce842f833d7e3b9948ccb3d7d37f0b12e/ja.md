```
index_map, num_segments = felzenszwalb(edges, num_vertices, k, min_size=0)
```

Felzenszwalbのセグメンテーションアルゴリズムを使用して、領域隣接グラフ（RAG）として表現された画像をセグメント化します。各ピクセル/領域はグラフのノードに対応し、各エッジの重みはピクセル間の非類似性を測定します。この関数は、セグメントの数とRAGのノードからセグメントへのインデックスマッピングを返します。

パラメータ：

  * `edges`:        RAG内のエッジの配列。各エッジは`ImageEdge`として表されます。
  * `num_vertices`: RAG内の頂点の数
  * `k`:            領域マージステップのしきい値。しきい値が大きいほど、セグメントは大きくなります。
  * `min_size`:     最小セグメントサイズ（ピクセル数）
