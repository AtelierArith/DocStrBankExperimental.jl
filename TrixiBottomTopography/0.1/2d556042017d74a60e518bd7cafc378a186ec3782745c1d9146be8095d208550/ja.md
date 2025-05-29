```
LinearBSpline(path::String)
```

`LinearBSpline`(@ref)のための`x`および`y`値を.txtファイルから読み込む関数です。入力値は次のとおりです。

  * `path`: 特定の.txtファイルのパスの文字列

.txtファイルは、この関数によって解釈されるために次の構造を持っている必要があります。

  * 最初の行: コメント `# x値の数`
  * 2行目: `x`値の数を示す整数
  * 3行目: コメント `# x値`
  * 続く行: 各値が独自の行を持つ`x`値
  * x値の後の行: コメント `# y値`
  * 残りの行: 各値が独自の行を持つ`y`値

`x`値と`y`値の数は同じである必要があることに注意してください。例は[こちら](https://gist.githubusercontent.com/maxbertrand1996/b05a90e66025ee1ebddf444a32c3fa01/raw/90d375c1ac11b26589aab1fe92bd0e6f6daf37b7/Rhine_data_1D_10.txt)で見つけることができます。
