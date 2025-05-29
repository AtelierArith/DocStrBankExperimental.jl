```
quantile(chains[; q = [0.025, 0.25, 0.5, 0.75, 0.975], append_chains = true, kwargs...])
```

チェーン内の各パラメータの分位数を計算します。

`append_chains=false`を設定すると、各チェーンの分位数を含むデータフレームのベクトルが返されます。
