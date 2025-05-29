```
CubicBSpline(path::String; end_condition = "free", smoothing_factor = 0.0)
```

`CubicBSpline`(@ref)のための`x`および`y`値を.txtファイルから読み込む関数です。入力値は次の通りです：

  * `path`: 特定の.txtファイルのパスの文字列
  * `end_condition`: `free`または`not-a-knot`のいずれかの文字列で、考慮すべき端条件を定義します。デフォルトでは`free`に設定されています。
  * `smoothing_factor`: Float64 $\geq$ 0.0で、`y`値の平滑化の度合いを指定します。デフォルトではこの値は`0.0`に設定されており、平滑化は行われません。

この関数によって解釈されるためには、.txtファイルは次の構造を持っている必要があります：

  * 最初の行: コメント `# Number of x values`
  * 二行目: `x`値の数を示す整数
  * 三行目: コメント `# x values`
  * 続く行: 各値が独自の行を持つ`x`値
  * `x`値の後の行: コメント `# y values`
  * 残りの行: 各値が独自の行を持つ`y`値

`x`値と`y`値の数は同じである必要があることに注意してください。例は[こちら](https://gist.githubusercontent.com/maxbertrand1996/b05a90e66025ee1ebddf444a32c3fa01/raw/90d375c1ac11b26589aab1fe92bd0e6f6daf37b7/Rhine_data_1D_10.txt)にあります。
