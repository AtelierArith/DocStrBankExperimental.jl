```
XPRSslpchgcoef(prob, row, col, factor, parsed, type, value)::prob
```

解析済みまたは未解析の式を使用して、単一の行列係数を追加または変更します。

この関数の簡易版については、XSLPchgformulaを参照してください。

# 引数

  * `prob::XPRSprob`: 現在のSLP問題。
  * `row::Integer`: 係数の行列行のインデックス。
  * `col::Integer`: 係数の行列列のインデックス。
  * `factor::Union{Nothing,Float64}`: 式の定数乗数を保持する倍精度変数のアドレス。
  * `parsed::Integer`: トークン配列が内部未解析（`parsed`=0）または内部解析済み逆ポーランド（`parsed`=1）としてフォーマットされているかを示す整数。
  * `type::AbstractVector{Integer}`: 各項目の説明と式を提供するトークンタイプの配列。
  * `value::AbstractVector{Number}`: `type`のタイプに対応する値の配列。

# 戻り値

  * `prob::XPRSprob`: 現在のSLP問題。

C APIの対応する関数[XPRSslpchgcoef](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSslpchgcoef.html)のドキュメントも参照してください。
