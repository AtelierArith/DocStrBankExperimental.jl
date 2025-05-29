```
XPRSnlploadformulas(prob, nnlpcoefs, rowind, formulastart, parsed, type, value)::prob
```

非線形の数式をSLP問題にロードします

# 引数

  * `prob::XPRSprob`: 現在のSLP問題。
  * `nnlpcoefs::Integer`: ロードする非線形係数の数。
  * `rowind::AbstractVector{Integer}`: 係数の行のインデックスを保持する整数配列。
  * `formulastart::AbstractVector{Integer}`: 係数のための`type`と`value`の配列における開始位置を保持する長さ`nnlpcoefs+1`の整数配列。
  * `parsed::Integer`: トークン配列が内部未解析形式（`parsed`=0）または内部解析済み逆ポーランド形式（`parsed`=1）としてフォーマットされているかを示す整数。
  * `type::AbstractVector{Integer}`: 各係数の数式を提供するトークンタイプの配列。
  * `value::AbstractVector{Number}`: `type`のタイプに対応する値の配列。

# 戻り値

  * `prob::XPRSprob`: 現在のSLP問題。

C APIの対応する関数[XPRSnlploadformulas](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSnlploadformulas.html)のドキュメントも参照してください。
