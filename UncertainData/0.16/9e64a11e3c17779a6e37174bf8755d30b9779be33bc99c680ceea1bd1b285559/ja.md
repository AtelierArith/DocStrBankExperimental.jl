```
example_uncertain_indexvalue_datasets(system::DynamicalSystems.DiscreteDynamicalSystem, n::Int, vars; Ttr = 1000,
    d_xval = Uniform(0.01, 0.4), d_yval = Uniform(0.01, 0.5),
    d_xind = Uniform(0.5, 1.5), d_yind = Uniform(0.5, 1.5))
```

離散動的 `system` から `UncertainIndexValueDataset` のペアを生成します。これは、トランジェントランの `Ttr` ステップの後にシステムを `n` 回反復することによって生成され、`vars` の位置にある列（2つの列インデックスである必要があります）を別々の時系列として収集します。

各時系列を `x` と `y` と呼び、これらは不確実な値に変換されます。具体的には、`x[i]` と `y[i]` を `UncertainValue(Normal, x[i], rand(d_xval))` と `UncertainValue(Normal, y[i], rand(d_yval))` に置き換えます。時系列には明示的な時間インデックスが関連付けられていないため、`1:tstep:length(x)*tstep` の範囲としていくつかの時間インデックスを作成し、これを `x_inds` と `y_inds` と呼びます。`x` と `y` の時間インデックスも正規分布に従い、`x_inds[i] = UncertainValue(Normal, i, rand(d_xind))` とし、`y_inds` についても同様です。

`x` と `y` のそれぞれに対して `UncertainIndexValueDataset` インスタンスのタプルを返します。
