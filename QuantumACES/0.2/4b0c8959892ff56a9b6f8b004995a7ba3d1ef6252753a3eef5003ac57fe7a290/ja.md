```
pretty_print(io::IO, aces_data::ACESData, merit::Merit; projected::Bool = false)
pretty_print(aces_data::ACESData, merit::Merit; projected::Bool = false)
```

`aces_data`内のGLS、WLS、およびOLS推定器のゲート固有値推定器ベクトルの正規化RMS誤差のzスコアを、meritデータの予測を使用して印刷します。`projected`が`true`の場合は、投影されたゲート固有値推定器ベクトルのzスコアを印刷します。
