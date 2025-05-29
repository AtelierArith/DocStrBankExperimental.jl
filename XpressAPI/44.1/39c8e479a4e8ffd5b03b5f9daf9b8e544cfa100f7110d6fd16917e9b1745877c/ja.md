```
XPRSnlpevaluateformula(prob, parsed, type, values)::value
```

現在の変数の値を使用して式を評価します

# 引数

  * `prob::XPRSprob`: 現在のSLP問題。
  * `parsed::Integer`: 項目の式が内部未解析形式（`parsed`=0）であるか、解析済み（逆ポーランド）形式（`parsed`=1）であるかを示す整数。
  * `type::AbstractVector{Integer}`: 式のトークンタイプの整数配列。
  * `values::AbstractVector{Number}`: `type`に対応する値の倍精度配列。

# 戻り値

  * `value::Float64`: 計算結果を受け取るための倍精度値のアドレス。

C APIの対応する関数のドキュメントも参照してください [XPRSnlpevaluateformula](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSnlpevaluateformula.html)。
