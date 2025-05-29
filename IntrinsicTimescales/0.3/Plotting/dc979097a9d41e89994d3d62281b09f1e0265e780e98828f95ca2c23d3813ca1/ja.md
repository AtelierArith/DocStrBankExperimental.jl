```
plot(container::ABCResults, model::Models.AbstractTimescaleModel; show::Bool=true)
```

ABC結果の事後予測チェックをプロットします。データの要約統計（ACFまたはPSD）と重ね合わせた事後予測サンプルを表示します。

# 引数

  * `container::ABCResults`: ABC結果を含むコンテナ
  * `model::Models.AbstractTimescaleModel`: 推論に使用されるモデル
  * `show::Bool=true`: プロットを表示するかどうか
  * `n_samples::Int=100`: 予測に使用する事後サンプルの数

# 戻り値

  * プロットオブジェクト
