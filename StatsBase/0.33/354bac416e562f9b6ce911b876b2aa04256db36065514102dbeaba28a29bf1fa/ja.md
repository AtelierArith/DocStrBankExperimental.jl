```
AnalyticWeights(vs, wsum=sum(vs))
```

重み値 `vs` を持つ `AnalyticWeights` ベクトルを構築します。事前に計算された合計は `wsum` として提供できます。

アナリティックウェイトは、各観測値に対する非ランダムな相対的重要性（通常は 0 と 1 の間）を示します。これらの重みは、信頼性重み、精度重み、または逆分散重みとも呼ばれることがあります。これらは通常、重み付けされる観測値が異なる分散を持つ集計値（例：平均値）である場合に使用されます。
