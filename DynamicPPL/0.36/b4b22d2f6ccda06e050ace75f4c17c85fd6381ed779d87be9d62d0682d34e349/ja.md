```
extract_priors(model::Model, varinfo::AbstractVarInfo)
```

モデルから事前分布を抽出します。

これは、`varinfo` に存在する値でモデルを評価し、各チルダステートメントに存在する分布を記録することによって行われます。
