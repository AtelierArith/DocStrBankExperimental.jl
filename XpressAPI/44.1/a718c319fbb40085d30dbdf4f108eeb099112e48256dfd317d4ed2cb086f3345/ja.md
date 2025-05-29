```
XPRSnlpchgformula(prob, row, parsed, type, value)::prob
```

解析済みまたは未解析の数式を使用して、単一の行列数式を追加または置き換えます。

# 引数

  * `prob::XPRSprob`: 現在のSLP問題。
  * `row::Integer`: 係数のための行列行のインデックス。
  * `parsed::Integer`: トークン配列が内部未解析（`parsed`=0）としてフォーマットされているか、内部解析済み逆ポーランド（`parsed`=1）としてフォーマットされているかを示す整数。
  * `type::AbstractVector{Integer}`: 各アイテムの説明と数式を提供するトークンタイプの配列。
  * `value::AbstractVector{Number}`: `type`内のタイプに対応する値の配列。

# 戻り値

  * `prob::XPRSprob`: 現在のSLP問題。

C APIの対応する関数[XPRSnlpchgformula](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSnlpchgformula.html)のドキュメントも参照してください。
