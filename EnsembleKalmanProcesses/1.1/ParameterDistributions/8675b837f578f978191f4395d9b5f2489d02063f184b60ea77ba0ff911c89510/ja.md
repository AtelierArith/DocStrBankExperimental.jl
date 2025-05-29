```
sample([rng], d::VectorOfParameterized, [n_draws])
```

パラメータ分布 `d` から `n_draws` サンプルを引きます。パラメータを列として持つ配列を返します。`rng` はオプションで、デフォルトは `Random.GLOBAL_RNG` です。`n_draws` もオプションで、デフォルトは 1 です。計算空間で実行されます。
