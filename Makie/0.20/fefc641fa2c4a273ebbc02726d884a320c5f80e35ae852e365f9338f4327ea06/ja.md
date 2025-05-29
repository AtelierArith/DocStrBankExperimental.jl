```
boxplot(x, y; kwargs...)
```

Tukeyスタイルのボックスプロットを描画します。ボックスプロットには3つのコンポーネントがあります：

  * 中線が中央値を示す四分位範囲（IQR）を跨ぐ`crossbar`
  * `range * iqr`を跨ぐ`errorbar`のひげ
  * ひげの外側にあるデータ、すなわち外れ値を示す点

# 引数

  * `x`: カテゴリの位置
  * `y`: ボックス内の変数

# キーワード

  * `weights`: 統計的重みのベクトル（データの長さ）。デフォルトでは、各観測値の重みは`1`です。
  * `orientation=:vertical`: ボックスの向き（`:vertical`または`:horizontal`）
  * `width=1`: 縮小前のボックスの幅
  * `gap=0.2`: 縮小係数、`width -> width * (1 - gap)`
  * `show_notch=false`: ノッチを描画する
  * `notchwidth=0.5`: ノッチの最狭幅のための`width`の乗数
  * `show_median=true`: 中線として中央値を表示する
  * `range`: ひげの長さを制御するIQRの倍数
  * `whiskerwidth`: ひげのTの幅のための`width`の乗数、または`width`に合わせるための`:match`
  * `show_outliers`: 外れ値を点として表示する
  * `dodge`: 同じ`x`位置に複数の並んだボックスを作成するためのグループ化変数の`Integer`のベクトル（データの長さ）
  * `dodge_gap = 0.03`: ドッジされたボックス間の間隔
