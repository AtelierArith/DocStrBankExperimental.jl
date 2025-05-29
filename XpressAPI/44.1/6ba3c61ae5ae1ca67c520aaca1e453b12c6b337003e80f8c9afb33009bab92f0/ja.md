```
XPRSnlpgetformulastr(prob, row, maxbytes)::formula, nbytes
```

単一の行列式を文字列として取得します。

# 引数

  * `prob::XPRSprob`: 現在のSLP問題。
  * `row::Integer`: 式の行インデックスを保持する整数。
  * `maxbytes::Integer`: `formula`バッファの長さ。

# 戻り値

  * `formula::AbstractString`: 式がファイルからの入力に使用されるのと同じ形式で配置される文字バッファ。
  * `nbytes::Int32`: ヌル終端子を含まない式の長さに設定されます。

C APIの対応する関数[XPRSnlpgetformulastr](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSnlpgetformulastr.html)のドキュメントも参照してください。
