```
XPRSslpchgdeltatype(prob, nvars, varind, deltatypes, values)::prob
```

非線形変数に割り当てられたデルタのタイプを変更します。

# 引数

  * `prob::XPRSprob`: 現在のSLP問題。
  * `nvars::Integer`: デルタタイプを変更するSLP変数の数。
  * `varind::AbstractVector{Integer}`: デルタを変更する変数のインデックス。
  * `deltatypes::AbstractVector{Integer}`: デルタ変数のタイプ: 0微分可能変数、デフォルト。
  * `values::AbstractVector{Number}`: 変数のグリッドまたは最小ステップサイズ。

# 戻り値

  * `prob::XPRSprob`: 現在のSLP問題。

C APIの対応する関数のドキュメントも参照してください [XPRSslpchgdeltatype](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSslpchgdeltatype.html)。
