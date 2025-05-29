```
XPRSslpchgccoef(prob, row, col, factor, formula)::prob
```

**非推奨** XPRSslpchgcoefstrの使用を推奨します。

文字列を使用して単一の行列係数を追加または変更します。この関数の簡易版については、XPRSnlpchgformulastrを参照してください。

# 引数

  * `prob::XPRSprob`: 現在のSLP問題。
  * `row::Integer`: 係数のための行列行のインデックス。
  * `col::Integer`: 係数のための行列列のインデックス。
  * `factor::Union{Nothing,Float64}`: 公式の定数乗数を保持する倍精度変数のアドレス。
  * `formula::Union{Nothing,AbstractString}`: トークンがスペースで区切られた公式を保持する文字列。

# 戻り値

  * `prob::XPRSprob`: 現在のSLP問題。

C APIの対応する関数[XPRSslpchgccoef](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSslpchgccoef.html)のドキュメントも参照してください。
