```
crossbar(x, y, ymin, ymax; kwargs...)
```

クロスバーを描画します。クロスバーは、（潜在的に切り欠きのある）ボックスを持つ範囲を表します。最も一般的には `boxplot` の一部として使用されます。

# 引数

  * `x`: ボックスの位置
  * `y`: ボックス内の中線の位置
  * `ymin`: ボックスの下限
  * `ymax`: ボックスの上限

# キーワード

  * `orientation=:vertical`: ボックスの向き（`:vertical` または `:horizontal`）
  * `width=1`: 縮小前のボックスの幅
  * `gap=0.2`: 縮小係数、`width -> width * (1 - gap)`
  * `show_notch=false`: 切り欠きを描画するかどうか
  * `notchmin=automatic`: 切り欠きの下限
  * `notchmax=automatic`: 切り欠きの上限
  * `notchwidth=0.5`: 最も狭い切り欠きの幅のための `width` の乗数
  * `show_midline=true`: 中線を表示するかどうか
