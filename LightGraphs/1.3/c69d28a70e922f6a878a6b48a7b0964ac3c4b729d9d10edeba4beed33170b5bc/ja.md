```
maxsimplecycles(dg::::IsDirected, byscc::Bool = true)
```

有向グラフ `dg` における理論的な最大サイクル数を計算します。

計算は、グラフが完全であると仮定するか、強連結成分の分解を考慮することができます（`byscc` パラメータ）。

### パフォーマンス

より効率的なバージョンが可能です。

### 参考文献

  * [Johnson](http://epubs.siam.org/doi/abs/10.1137/0204007)
