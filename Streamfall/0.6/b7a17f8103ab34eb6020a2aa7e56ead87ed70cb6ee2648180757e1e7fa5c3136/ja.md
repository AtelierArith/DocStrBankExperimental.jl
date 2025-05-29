```
calc_effective_rainfall(
    rainfall::Float64, cmd::Float64, d::Float64,
    d2::Float64; n::Float64=0.1
)::Float64
```

有効降雨量を推定します。

# 参考文献

  * Croke, B.F.W., Jakeman, A.J. 2004 IHACRES降雨-流出モデルのための流域水分不足モジュール, 環境モデリング & ソフトウェア, 19(1), pp. 1-5. doi: 10.1016/j.envsoft.2003.09.001
  * Croke, B.F.W., Jakeman, A.J. 2005 "IHACRES降雨-流出モデルのための流域水分不足モジュール [Environ. Model. Softw. 19 (1) (2004) 1-5]" の訂正, 環境モデリング & ソフトウェア, 20(7), p. 997. doi: https://doi.org/10.1016/j.envsoft.2004.11.004

# 引数

  * `rainfall`: 時間ステップの降雨量
  * `cmd`: 前のCMD値
  * `d`: 閾値
  * `d2`: `d`に適用されるスケーリングファクター
  * `n`: スケーリングファクター（デフォルト = 0.1）。デフォルト値はほとんどのケースに適しています（Croke & Jakeman, 2004）

# 戻り値

  * 有効降雨量の値
