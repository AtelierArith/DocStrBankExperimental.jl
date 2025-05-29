```
XPRSnlpchgformulastr(prob, row, formula)::prob
```

文字列を使用して単一の行列式を追加または置き換えます。

# 引数

  * `prob::XPRSprob`: 現在の問題。
  * `row::Integer`: 係数のための行列行のインデックス。
  * `formula::Union{Nothing,AbstractString}`: トークンがスペースで区切られた式を保持する文字列。

# 戻り値

  * `prob::XPRSprob`: 現在の問題。

C APIの対応する関数[XPRSnlpchgformulastr](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSnlpchgformulastr.html)のドキュメントも参照してください。
