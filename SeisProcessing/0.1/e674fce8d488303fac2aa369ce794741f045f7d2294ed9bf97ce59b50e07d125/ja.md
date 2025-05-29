```
SeisBandPass(in; <キーワード引数>)
```

地震データにバンドパスフィルターを適用します。入力および出力データはtxドメインの2Dです。フィルターはfxドメインで適用されます。

# 引数

  * `in`: txドメインの入力2Dデータ配列。時間が最初の次元です。

# キーワード引数

  * `dt=0.004`: 時間サンプリング間隔（秒）。
  * `fa=0`: 下限周波数カット [Hz]
  * `fb=0`: 下限周波数バンドパス [Hz]
  * `fc=60`: 上限周波数バンドパス [Hz]
  * `fd=80`: 上限周波数カット [Hz]

# 例

```
julia> d = SeisLinearEvents(); SeisPlotAmplitude(d,125,0.004);
julia> d_filter = SeisBandPass(d;dt=0.004,fa=2,fb=8,fc=12,fd=20); SeisPlotAmplitude(d_filter,125,0.004)
julia> SeisPlot([d d_filter],title="データとフィルタリングされたデータ")

```
