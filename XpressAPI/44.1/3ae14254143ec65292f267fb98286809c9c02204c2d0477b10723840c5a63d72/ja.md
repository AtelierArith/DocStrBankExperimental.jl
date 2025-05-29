```
XPRSslpchgcoefstr(prob, row, col, factor, formula)::prob
```

文字列を使用して単一の行列係数を追加または変更します。

この関数の簡易版については、XPRSnlpchgformulastrを参照してください。

# 引数

  * `prob::XPRSprob`: 現在の問題。
  * `row::Integer`: 係数のための行列行のインデックス。
  * `col::Integer`: 係数のための行列列のインデックス。
  * `factor::Union{Nothing,Float64}`: 定数乗数を保持する倍精度変数のアドレス。
  * `formula::Union{Nothing,AbstractString}`: トークンがスペースで区切られた式を保持する文字列。

# 戻り値

  * `prob::XPRSprob`: 現在の問題。

C APIの対応する関数[XPRSslpchgcoefstr](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSslpchgcoefstr.html)のドキュメントも参照してください。
