```
ProbabilityWeights(vs, wsum=sum(vs))
```

重み値 `vs` を持つ `ProbabilityWeights` ベクトルを構築します。事前に計算された合計を `wsum` として提供することもできます。

確率重みは、各観察のサンプリング確率の逆数を表し、特定の人口グループの過剰または過少サンプリングに対する補正メカニズムを提供します。これらの重みは、サンプリング重みとも呼ばれることがあります。
