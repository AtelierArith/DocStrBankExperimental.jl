```
predict_proba(mix::MixtureModel, y::AbstractVecOrMat; robust=false)
```

`MixtureModel`に基づいて、各観測値がカテゴリに属する確率を評価します。

  * `robust = true`は、(対数)尤度が`-∞`（または`∞`）にアンダーフロー（オーバーフロー）するのを防ぎます。
