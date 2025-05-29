```
function runLMEM(formula,userData,nChain,nBurn,nThin;myHints=Dict{Symbol,Any}(),blockThese=[],outFolder="outMCMC",VCV=[],userPedData=[],summaryStat=Dict{Any,Any}())
```

  * `formula` は [`StatsModels.jl`](https://juliastats.org/StatsModels.jl/latest/) パッケージによって提供されるモデル方程式です
  * `userData` は `lhs` および `rhs` 変数を含む `DataFrame` です（`PED` および `SNP` によって定義されたもの以外）
  * `nChain`、`nBurn` および `nThin` は MCMC サンプリングに使用されるチェーンの長さ、バーンイン期間、および間引き間隔です
  * ユーザーは `myHints` を提供することで変数のコーディング（例：フルダミーコーディング）を定義できます。`StatsModels.jl` のマニュアルで [`categorical data`](https://juliastats.org/StatsModels.jl/latest/contrasts/#Modeling-categorical-data) を確認することが役立つかもしれません。
