```
XPRSaddnames(prob, type, names, first, last)::prob
```

モデルがロードされると、モデルの行、列、セット、区分的線形および一般的制約には名前が関連付けられていない場合があります。

これは、行、列、セット、区分的線形および一般的制約がその順序番号で参照できるため、重要ではないかもしれません。しかし、行、列、セット、区分的線形および一般的制約の名前をASCIIソリューションファイルに表示させたい場合、`XPRSaddnames`を使用して行/列/...の範囲に名前を追加できます。

# 引数

  * `prob::XPRSprob`: 現在の問題。
  * `type::Integer`: XPRS*NAMES*ROW`(=1)`は行名用; XPRS*NAMES*COLUMN`(=2)`は列名用; XPRS*NAMES*SET`(=3)`はセット名用; XPRS*NAMES*PWLCONS`(=4)`は区分的線形制約名用; XPRS*NAMES*GENCONS`(=5)`は一般的制約名用; XPRS*NAMES*OBJECTIVE`(=6)`は目的名用。
  * `names::AbstractVector{AbstractString}`: ヌル終端文字列名を含む文字バッファ。
  * `first::Integer`: 行、列、セット、区分的線形制約、一般的制約または目的の範囲の開始。
  * `last::Integer`: 行、列、セット、区分的線形制約、一般的制約または目的の範囲の終了。

# 戻り値

  * `prob::XPRSprob`: 現在の問題。

C APIの対応する関数のドキュメントも参照してください [XPRSaddnames](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSaddnames.html)。
