```
autocor(
    chains;
    append_chains = true,
    demean = true,
    [lags,]
    kwargs...,
)
```

各パラメータの自己相関をチェーンに対して計算します。

デフォルトの `lags` は `[1, 5, 10, 50]` で、`n` は推定に使用されるサンプル数であり、`n - 1` に上限があります。

`append_chains=false` を設定すると、各チェーンの自己相関を含むデータフレームのベクトルが返されます。
