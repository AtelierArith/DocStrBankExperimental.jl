```
function forward_pass_ICNN!(jump, input, output_var, input_vars)
```

ICNNを通過するフォワードパスを計算します（与えられた入力で生成される出力）。

# 引数

  * `jump`: ICNNを持つJuMPモデル
  * `input`: フォワードパスされる値
  * `output_var`: ICNN出力変数への参照
  * `input_vars`: ICNN入力変数への参照
