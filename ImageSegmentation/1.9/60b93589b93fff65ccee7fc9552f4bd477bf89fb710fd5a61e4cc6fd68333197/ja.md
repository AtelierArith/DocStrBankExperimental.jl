```
seg2 = merge_segments(seg, threshold)
```

[`SegmentedImage`](@ref)内のセグメントを、領域隣接グラフ（RAG）を構築し、重みが `threshold` 未満のエッジで接続されたセグメントをマージすることによってマージします。

# 引数:

  * `seg`         : マージされるセグメント画像。
  * `threshold`   : セグメントをマージする際に考慮する隣接セグメントの色の違いの上限。

# 引用:

Vighnesh Birodkar "Hierarchical merging of region adjacency graphs" https://vcansimplify.wordpress.com/2014/08/17/hierarchical-merging-of-region-adjacency-graphs/
