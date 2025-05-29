```
XPRSaddsetnames(prob, names, first, last)::prob
```

MIPエンティティを持つモデルがロードされると、特別な順序付きセットに関連付けられた名前がない場合があります。

ASCIIソリューションファイルに名前を表示させたい場合は、この関数を使用してセットの範囲に名前を追加できます。

# 引数

  * `prob::XPRSprob`: 現在の問題。
  * `names::AbstractVector{AbstractString}`: ヌル終端文字列名を含む文字バッファ。
  * `first::Integer`: セットの範囲の開始。
  * `last::Integer`: セットの範囲の終了。

# 戻り値

  * `prob::XPRSprob`: 現在の問題。

C APIの対応する関数[XPRSaddsetnames](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSaddsetnames.html)のドキュメントも参照してください。
