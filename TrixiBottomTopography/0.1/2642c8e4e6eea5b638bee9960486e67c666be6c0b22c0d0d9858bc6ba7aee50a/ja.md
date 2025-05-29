```
BicubicBSpline(path::String; end_condition = "free", smoothing_factor = 0.0)
```

`BilinearBSpline`(@ref)からの`x`、`y`、`z`値を.txtファイルから読み込む関数です。入力値は次の通りです：

  * `path`: 特定の.txtファイルのパスの文字列
  * `end_condition`: "free"または"not-a-knot"のいずれかの文字列で、考慮すべき端条件を定義します。デフォルトでは"free"に設定されています。
  * `smoothing_factor`: Float64 $\geq$ 0.0で、`y`値の平滑化の度合いを指定します。デフォルトではこの値は0.0に設定されており、平滑化は行われません。

この関数によって解釈されるためには、.txtファイルは次の構造を持っている必要があります：

  * 最初の行: コメント `# Number of x values`
  * 第二の行: `x`値の数を示す整数
  * 第三の行: コメント `# Number of y values`
  * 第四の行: `y`値の数を示す整数
  * 第五の行: コメント `# x values`
  * 続く行: 各値が独自の行を持つ`x`値
  * `x`値の後の行: コメント `# y values`
  * 続く行: 各値が独自の行を持つ`y`値
  * `y`値の後の行: コメント `# z values`
  * 残りの行: 各値が独自の行を持つ`z`値で、次の順序で配置されています：z*11, z*12, ... z*1n, z*21, ... z*2n, ..., z*m1, ..., z_mn

例は[こちら](https://gist.githubusercontent.com/maxbertrand1996/7b1b943eac142d5bc836bb818fe83a5a/raw/74228e349e91fbfe1563479f99943b469f26ac62/Rhine_data_2D_10.txt)で見つけることができます。
