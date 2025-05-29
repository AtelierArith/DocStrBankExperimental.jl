```
community_detection_nback(g, k)
```

グラフ `g` の非バックトラッキング行列のスペクトル特性を使用したコミュニティ検出 (詳細は [Krzakala et al.](http://www.pnas.org/content/110/52/20935.short) を参照)。 `k` は検出するコミュニティの数です。

関連するコミュニティ検出アルゴリズムについては [`community_detection_bethe`](@ref) を参照してください。

コミュニティ内の頂点割り当てを含むベクトルを返します。
