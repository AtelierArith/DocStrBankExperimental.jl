```
LazyNBProportionalBandSpectrum{NO,IsTonal}(f1_nb, df_nb, msp_amp, cbands::AbstractProportionalBands{NO,:center})
```

狭帯域スペクトルから比例中心バンド `cbands` を持つ比例バンドスペクトルの遅延表現を構築します。

狭帯域周波数は、最初の狭帯域周波数 `f1_nb` と狭帯域周波数間隔 `df_nb` によって定義されます。`msp_amp` は狭帯域平均二乗圧力振幅のスペクトルです。

`IsTonal` は、音響エネルギーが狭い周波数バンドを通じてどのように分配されるかを示します：

  * `IsTonal == false` は、音響エネルギーが各バンド全体に均等に分配されると仮定されることを意味します
  * `IsTonal == true` は、音響エネルギーが各バンドの中心に集中していると仮定されることを意味します
