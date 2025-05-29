```
transitiveclosure!(g, selflooped=false)
```

有向グラフの推移閉包を計算します。DFSを使用します。`selflooped`がtrueの場合、グラフに自己ループを追加します。

### パフォーマンス

時間計算量は$\mathcal{O}(|E||V|)$です。

### 実装ノート

このバージョンの関数は元のグラフを変更します。
