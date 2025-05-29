```
function forward_pass_NN!(jump, input, output_var, input_vars)
```

NNを通じたフォワードパスを計算します（与えられた入力で生成される出力）。この関数は、NNの定式化がより大きな最適化問題に組み込まれているときに使用できます。

# 引数

  * `jump`: NN定式化を持つJuMPモデル
  * `input`: フォワードパスされる値
  * `output_var`: NN出力変数への参照
  * `input_vars`: NN入力変数への参照
