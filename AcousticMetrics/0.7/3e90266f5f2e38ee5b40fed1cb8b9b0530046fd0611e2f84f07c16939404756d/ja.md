```
LazyNBProportionalBandSpectrum(TBands::Type{<:AbstractProportionalBands}, f1_nb, df_nb, msp_amp, scaler=1, istonal::Bool=false)
```

`LazyNBProportionalBandSpectrum`を、比例バンド`TBands`と狭帯域平均二乗圧力振幅ベクトル`msp_amp`、およびオプションの比例バンド周波数スケーラー`scaler`を使用して構築します。

`f1_nb`は最初の非ゼロ狭帯域周波数であり、`df_nb`は狭帯域周波数の間隔です。`istonal`の`Bool`引数が`true`の場合、狭帯域スペクトルはトーナルであり、したがって離散周波数に集中しています。`false`の場合、スペクトルは各狭帯域周波数バンドで一定であると仮定されます。比例バンド周波数は`scaler`によってスケーリングされます。
