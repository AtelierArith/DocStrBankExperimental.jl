```
prepareData(df, confounderEps, confounderCov)
prepareData("path/to/filename.csv", confounderEps, confounderCov)
```

データの準備は、データ内のオブジェクトラベルから潜在的な交絡構造を作成します。観測された共変量、処置、および結果のための行列を解析します。

返すもの: `X, T, Y, SigmaU`
