```
SeisDiff(d ; <キーワード引数>)
```

周波数領域で地震トレースに微分を適用します。また、位相回転を適用するためにも使用できます。

# 引数

  * `d`: txドメインの入力2Dデータ配列。最初の次元は時間です。

# キーワード引数

  * `delay=0.1`: 秒単位の希望する時間遅延。
  * `pow=-2`: 微分の次数
  * `rot=0`: 定数位相シフトまたは回転

# 例

```
julia> d = SeisLinearEvents(); SeisPlotTX(d);
julia> d2 = SeisDiff(d;dt=0.004,pow=1); SeisPlotTX(d);
```
