```
dwt!(y, x, wt::OrthoFilter[, L=maxtransformlevels(x)])

dwt!(y, wt::GLS[, L=maxtransformlevels(x)])
```

`dwt`と同様ですが、配列の割り当ては行いません。フィルタを使用した「アウトオブプレイス」変換、またはリフティングスキームを使用したインプレース変換を実行します。フィルタとリフティングメソッドの違いは、変換アルゴリズムの構造によるものです。

**参照:** `idwt!`
