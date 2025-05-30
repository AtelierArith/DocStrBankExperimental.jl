```
boxplot(x, y; kwargs...)
```

Tukeyスタイルのボックスプロットを描画します。ボックスプロットには3つのコンポーネントがあります：

  * 中央値を示すミッドラインを持つ四分位範囲（IQR）を跨ぐ`crossbar`
  * `range * iqr`を跨ぐ`errorbar`のひげ
  * ひげの外にあるデータ、すなわち外れ値を示すポイント

# 引数

  * `x`: カテゴリの位置
  * `y`: ボックス内の変数

# キーワード

  * `orientation=:vertical`: ボックスの向き（`:vertical`または`:horizontal`）
  * `width=0.8`: ボックスの幅
  * `show_notch=false`: ノッチを描画するかどうか
  * `notchwidth=0.5`: ノッチの最狭幅に対する`width`の倍率
  * `show_median=true`: 中央値をミッドラインとして表示
  * `range`: ひげの長さを制御するIQRの倍数
  * `whiskerwidth`: ひげのTの幅に対する`width`の倍率、または`width`に合わせるための`:match`
  * `show_outliers`: 外れ値をポイントとして表示
