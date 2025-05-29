```
CommonLogDensity(nparameters, sample_init, lπ)
```

この関数は、`sample` 関数を介して古典的な MCMC を実行するための型を返します。

`nparameters`: サンプルごとのパラメータの総数。

`sample_init`: `RNG::AbstractRNG` を受け取り、`lπ` のサンプルを返す関数。

`lπ`: サンプルを受け取り、ログ密度の浮動小数点値を返す関数。
