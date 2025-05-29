```
LazyNBProportionalBandSpectrum(f1_nb, df_nb, msp_amp, cbands::AbstractProportionalBands{NO,:center}, istonal=false)
```

狭帯域スペクトルから比例バンドスペクトルの遅延表現を、比例中心バンド `cbands` を用いて構築します。

狭帯域周波数は、最初の狭帯域周波数 `f1_nb` と狭帯域周波数間隔 `df_nb` によって定義されます。`msp_amp` は狭帯域平均二乗圧力振幅のスペクトルです。

`istonal` は、音響エネルギーが狭い周波数バンドを通じてどのように分配されるかを示します：

  * `istonal == false` は、音響エネルギーが各バンド全体に均等に分配されると仮定されます
  * `istonal == true` は、音響エネルギーが各バンドの中心に集中していると仮定されます
