```
BartlettPeriodogram(timeseries, Δ, segmentlength)
```

提供された時系列に対して、サンプリングレートΔを用いてバートレット周期ogramを計算します。

# 引数

  * `timeseries`: 単変量の場合は`Vector`、多変量の場合は`n`行`d`列の`Matrix`で、ここで`n`は観測数、`d`は時系列の次元です。
  * `Δ`: 正の実数。
  * `segmentlength`: 各セグメントで使用される系列の長さ。

バートレット法を使用してスペクトル密度関数の推定値を計算します。`Periodogram`と同じ正規化を使用します。

# 外部リンク

  * [バートレット法 - Wikipedia](https://en.wikipedia.org/wiki/Bartlett%27s_method)
