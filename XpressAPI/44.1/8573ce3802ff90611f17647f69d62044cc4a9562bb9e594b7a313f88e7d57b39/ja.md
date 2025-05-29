```
XPRSgetnamelist(prob, type, first, last)::names
```

指定された範囲内の行、列、セット、区分線形制約、一般制約、または目的の名前を返します。

名前は文字バッファに返され、末尾の空白はなく、各名前は何もない文字で区切られます。

# 引数

  * `prob::XPRSprob`: 現在の問題。
  * `type::Integer`: 行名が必要な場合は`XPRS*NAMES*ROW`(=1)；列名が必要な場合は`XPRS*NAMES*COLUMN`(=2)；セット名が必要な場合は`XPRS*NAMES*SET`(=3)；区分線形制約名が必要な場合は`XPRS*NAMES*PWLCONS`(=4)；一般制約名が必要な場合は`XPRS*NAMES*GENCONS`(=5)；目的関数名が必要な場合は`XPRS*NAMES*OBJECTIVE`(=6)。
  * `first::Integer`: 範囲内の最初の行、列、セット、区分線形または一般制約。
  * `last::Integer`: 範囲内の最後の行、列、セット、区分線形または一般制約。

# 戻り値

  * `names::AbstractVector{AbstractString}`: 名前がヌル終端文字列のシーケンスとして返されるバッファ。

C APIの対応する関数[XPRSgetnamelist](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSgetnamelist.html)のドキュメントも参照してください。
