```julia
normlogpdf(mu, sigma, x)
```

平均 `mu` と標準偏差 `sigma` を持つ正規（ガウス）分布の確率密度関数の自然対数を `x` で評価したものです。

もし `x`、[`mu`、および `sigma`] が配列として与えられた場合、すべての `x` にわたる対数確率密度の合計が返されます。

関連情報として `normpdf`、`normlogpdf` を参照してください。
