```
predict(mix::MixtureModel, y::AbstractVector; robust=false)
```

`MixtureModel`に基づいて各観測値の最も可能性の高いカテゴリを評価します。

  * `robust = true`は、(対数)尤度が`-∞`または`∞`にオーバーフローするのを防ぎます。
