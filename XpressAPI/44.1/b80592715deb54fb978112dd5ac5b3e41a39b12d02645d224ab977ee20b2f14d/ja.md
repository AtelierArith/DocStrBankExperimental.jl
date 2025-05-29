```
XPRSnlpgetformulastring(prob, row, maxbytes)::formula
```

**非推奨**XPRSnlpgetformulastrの使用を推奨します。

文字列で単一の行列式を取得します。

# 引数

  * `prob::XPRSprob`: 現在のSLP問題。
  * `row::Integer`: 式の行インデックスを保持する整数。
  * `maxbytes::Integer`: 返される式の最大長。

# 戻り値

  * `formula::AbstractString`: 式がファイルからの入力に使用されるのと同じ形式で配置される文字バッファ。

C APIの対応する関数[XPRSnlpgetformulastring](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSnlpgetformulastring.html)のドキュメントも参照してください。
