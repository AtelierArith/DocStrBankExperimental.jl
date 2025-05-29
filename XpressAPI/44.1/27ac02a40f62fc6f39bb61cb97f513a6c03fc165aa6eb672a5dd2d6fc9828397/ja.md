```
XPRSaddmipsol(prob, len, solval, colind, name)::prob
```

最適化器に問題の新しい実行可能、非実行可能、または部分的なMIPソリューションを追加します。

# 引数

  * `prob::XPRSprob`: 現在の問題。
  * `len::Integer`: 値が提供される列の数。
  * `solval::AbstractVector{Number}`: ソリューション値を含む長さ`length`のダブル配列。
  * `colind::AbstractVector{Integer}`: `solval`で提供されたソリューション値の列インデックスを含む長さ`length`のオプション整数配列。
  * `name::Union{Nothing,AbstractString}`: ソリューションに関連付けるオプションの名前。

# 戻り値

  * `prob::XPRSprob`: 現在の問題。

C APIの対応する関数[XPRSaddmipsol](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSaddmipsol.html)のドキュメントも参照してください。
