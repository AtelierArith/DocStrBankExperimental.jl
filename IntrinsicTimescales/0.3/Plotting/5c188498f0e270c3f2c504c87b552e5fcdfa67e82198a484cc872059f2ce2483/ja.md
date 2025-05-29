```
posterior_predictive(container::ADVIResults, model::Models.AbstractTimescaleModel; show::Bool=true)
```

ADVI結果の事後予測チェックをプロットします。事後予測サンプルに重ねてデータの要約統計（ACFまたはPSD）を表示します。

# 引数

  * `container::ADVIResults`: ADVI結果を含むコンテナ
  * `model::Models.AbstractTimescaleModel`: 推論に使用されるモデル
  * `show::Bool=true`: プロットを表示するかどうか
  * `n_samples::Int=100`: 予測に使用する事後サンプルの数

# 戻り値

  * プロットオブジェクト
