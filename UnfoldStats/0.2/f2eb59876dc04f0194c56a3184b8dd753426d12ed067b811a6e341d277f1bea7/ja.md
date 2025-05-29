```
extract_coefs(model::UnfoldModel, predictor, basisname)
```

Unfoldモデルの特定の`predictor`と`basisname`に対する係数を返します。

予測変数の項を抽出するには、`predictor`はシンボルである必要があります。例えば、:continuous。切片を抽出するには、`predictor`は文字列である必要があります。すなわち、"(Intercept)"。

`basisname`は、`coeftable(model)`で見つけることができる基底名のいずれかと一致する必要があります。

注意: 予測変数に数式内で複数の項がある場合（例えば、スプラインセット、複数のレベルを持つカテゴリ変数、または相互作用）、すべての項の係数が返されます。

返される係数の次元は、チャネル x 時間 x 係数です。
