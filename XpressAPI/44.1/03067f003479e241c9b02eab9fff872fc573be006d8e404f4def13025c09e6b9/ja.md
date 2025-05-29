```
XPRSnlpvalidatevector(prob, solution)::suminf, sumscaledinf, objval
```

与えられた解に対する制約の実現可能性を検証します

# 引数

  * `prob::XPRSprob`: 現在のSLP問題。
  * `solution::AbstractVector{Number}`: チェックされる解ベクトルを含む長さ`XPRS_COLS`のベクトル。

# 戻り値

  * `suminf::Float64`: 不実現可能性の合計が返されるダブルへのポインタ。
  * `sumscaledinf::Float64`: スケーリングされた（相対的な）不実現可能性の合計が返されるダブルへのポインタ。
  * `objval::Float64`: ネット目的が返されるダブルへのポインタ。

C APIの対応する関数[XPRSnlpvalidatevector](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSnlpvalidatevector.html)のドキュメントも参照してください。
