```
XPRSslpaddcoefs(prob, ncoefs, rowind, colind, factor, formulastart, parsed, type, value)::prob
```

SLP問題に非線形係数を追加します。

この関数の簡易版はXSLPaddformulasを参照してください。

# 引数

  * `prob::XPRSprob`: 現在のSLP問題。
  * `ncoefs::Integer`: 追加する非線形係数の数。
  * `rowind::AbstractVector{Integer}`: 係数の行のインデックスを保持する整数配列。
  * `colind::AbstractVector{Integer}`: 係数の列のインデックスを保持する整数配列。
  * `factor::AbstractVector{Number}`: 式がスケーリングされる因子を保持する倍精度配列。
  * `formulastart::AbstractVector{Integer}`: 係数の式の`type`および`value`配列における開始位置を保持する長さ`ncoefs+1`の整数配列。
  * `parsed::Integer`: トークン配列が内部未解析形式（`parsed`=0）または内部解析済み逆ポーランド形式（`parsed`=1）としてフォーマットされているかを示す整数。
  * `type::AbstractVector{Integer}`: 各係数の式を提供するトークンタイプの配列。
  * `value::AbstractVector{Number}`: `type`のタイプに対応する値の配列。

# 戻り値

  * `prob::XPRSprob`: 現在のSLP問題。

C APIの対応する関数[XPRSslpaddcoefs](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSslpaddcoefs.html)のドキュメントも参照してください。
