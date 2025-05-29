```
edge = ImageEdge(index1, index2, weight)
```

領域隣接グラフにエッジを構築します。`index1` と `index2` は、個々のピクセル/ボクセルに対応する整数（`sub2ind` を介した線形インデックスの意味で）であり、`weight` はエッジの重み（ピクセル/ボクセル間の非類似性を測定します）。
