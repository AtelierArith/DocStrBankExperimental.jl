```
XPRSloadqp64(prob, probname, ncols, nrows, rowtype, rhs, rng, objcoef, start, collen, rowind, rowcoef, lb, ub, nobjqcoefs, objqcol1, objqcol2, objqcoef)::prob
```

オプティマイザーデータ構造に二次問題をロードするために使用されます。

このような問題は、制約には含まれないものの、目的関数に二次項を持つ場合があります。

# 引数

  * `prob::XPRSprob`: 現在の問題。
  * `probname::Union{Nothing,AbstractString}`: 問題の名前を含む最大MAXPROBNAMELENGTH文字の文字列。
  * `ncols::Integer`: 行列の構造列の数。
  * `nrows::Integer`: 行列の行数（目的行を含まない）。
  * `rowtype::AbstractVector{Cchar}`: 行のタイプを含む長さ`nrows`の文字配列: Lは`<=`制約を示す; Eは=制約を示す; Gは`>=`制約を示す; Rは範囲制約を示す; Nは非拘束制約を示す。
  * `rhs::AbstractVector{Number}`: 行の右辺係数を含む長さ`nrows`の倍精度配列。
  * `rng::AbstractVector{Number}`: 範囲行の範囲値を含む長さ`nrows`の倍精度配列。
  * `objcoef::AbstractVector{Number}`: 目的関数の係数を含む長さ`ncols`の倍精度配列。
  * `start::AbstractVector{Integer}`: 各列の要素の開始位置の`rowind`および`rowcoef`配列内のオフセットを含む整数配列。
  * `collen::AbstractVector{Integer}`: 各列の非ゼロ要素の数を含む長さ`ncols`の整数配列。
  * `rowind::AbstractVector{Integer}`: 各列の非ゼロ要素の行インデックスを含む整数配列。
  * `rowcoef::AbstractVector{Number}`: 非ゼロ要素の値を含む倍精度配列; `rowind`と同じ長さ。
  * `lb::AbstractVector{Number}`: 列の下限を含む長さ`ncols`の倍精度配列。
  * `ub::AbstractVector{Number}`: 列の上限を含む長さ`ncols`の倍精度配列。
  * `nobjqcoefs::Integer`: 二次項の数。
  * `objqcol1::AbstractVector{Integer}`: 各二次項の最初の変数の列インデックスを含むサイズ`nobjqcoefs`の整数配列。
  * `objqcol2::AbstractVector{Integer}`: 各二次項の2番目の変数の列インデックスを含むサイズ`nobjqcoefs`の整数配列。
  * `objqcoef::AbstractVector{Number}`: 二次係数を含むサイズ`nobjqcoefs`の倍精度配列。

# 戻り値

  * `prob::XPRSprob`: 現在の問題。

C APIの対応する関数[XPRSloadqp64](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSloadqp64.html)のドキュメントも参照してください。
