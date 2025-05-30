```
ges(X; method=:gaussian_bic, penalty=0.5, parallel=false, verbose=false)
```

与えられた観測データ `X`（列に変数がある）を使用して、GESによる因果グラフを計算します。CPDAG、空のグラフに対するスコアの改善、および第一段階と第二段階の時間測定を返します。
