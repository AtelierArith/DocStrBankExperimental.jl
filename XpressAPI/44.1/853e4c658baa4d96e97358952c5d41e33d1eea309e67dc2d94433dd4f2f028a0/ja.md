```
XPRSslploadcoefs(prob, ncoefs, rowind, colind, factor, formulastart, parsed, type, coef)::prob
```

SLP問題に非線形係数をロードします。

この関数の簡易版はXSLPloadformulasを参照してください。

# 引数

  * `prob::XPRSprob`: 現在のSLP問題。
  * `ncoefs::Integer`: ロードする非線形係数の数。
  * `rowind::AbstractVector{Integer}`: 係数の行のインデックスを保持する整数配列。
  * `colind::AbstractVector{Integer}`: 係数の列のインデックスを保持する整数配列。
  * `factor::AbstractVector{Number}`: 数式がスケーリングされる因子を保持する倍精度配列。
  * `formulastart::AbstractVector{Integer}`: 係数の数式の`type`および`coef`配列における開始位置を保持する長さ`ncoefs+1`の整数配列。
  * `parsed::Integer`: トークン配列が内部未解析形式（`parsed`=0）または内部解析済み逆ポーランド形式（`parsed`=1）としてフォーマットされているかを示す整数。
  * `type::AbstractVector{Integer}`: 各係数の数式を提供するトークンタイプの配列。
  * `coef::AbstractVector{Number}`: `type`のタイプに対応する値の配列。

# 戻り値

  * `prob::XPRSprob`: 現在のSLP問題。

C APIの対応する関数[XPRSslploadcoefs](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSslploadcoefs.html)のドキュメントも参照してください。
