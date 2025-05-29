```
dominating_set(g, DegreeDominatingSet())
```

貪欲ヒューリスティックを使用して[支配集合](https://en.wikipedia.org/wiki/Dominating_set)を取得します。

### 実装ノート

頂点は、支配集合に含まれているか、支配集合の頂点に隣接している場合に支配されていると言います。支配集合を空の集合として初期化し、支配されていない頂点を最も多く支配する頂点を反復的に選択します。

### パフォーマンス

実行時間: $\mathcal{O}((|V|+|E|)*log(|V|))$ メモリ: $\mathcal{O}(|V|)$ 近似係数: `ln(maximum(degree(g)))+2`
