```
_comp_psd_lombscargle(times, data, frequency_grid)
```

単一の時系列のためのロムバ-スカーグル周期グラムを計算する内部関数。

# 引数

  * `times`: 時間点ベクトル（NaNなし）
  * `data`: 時系列データ（NaNなし）
  * `frequency_grid`: 事前計算された周波数グリッド

# 戻り値

  * `power`: ロムバ-スカーグル周期グラムの値
  * `frequency_grid`: 入力周波数グリッド

# 注意事項

  * コア計算にはLombScargle.jlを使用
  * データは事前処理されており、NaN値を含まないと仮定
  * 分散によってパワースペクトルを正規化

```
