```
community_detection_nback(g::AbstractGraph, k::Int)
```

グラフ `g` に対して `k` 個のコミュニティを検出するためのコミュニティ割り当てを含む、頂点によってインデックス付けされた配列を返します。コミュニティ検出は、`g` の非バックトラッキング行列のスペクトル特性を使用して行われます。

### 参考文献

  * [Krzakala et al.](http://www.pnas.org/content/110/52/20935.short)
