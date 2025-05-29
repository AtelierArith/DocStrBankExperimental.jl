```
dynamicmodelpredict(data::RheoFreqData, model::RheoModel)
```

周波数のみの動的レオロジーデータと、パラメータが置き換えられたモデルを考慮します。引数として与えられた周波数とモデルに基づいて予測された `Gp` と `Gpp` を持つ別の `RheoFreqData` インスタンスを返します。
