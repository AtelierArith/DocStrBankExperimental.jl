```
XPRSloadqcqp(prob, probname, ncols, nrows, rowtype, rhs, rng, objcoef, start, collen, rowind, rowcoef, lb, ub, nobjqcoefs, objqcol1, objqcol2, objqcoef, nqrows, qrowind, nrowqcoef, rowqcol1, rowqcol2, rowqcoef)::prob
```

二次制約を持つ二次問題をオプティマイザデータ構造にロードするために使用されます。

このような問題は、目的関数および制約に二次項を持つ場合があります。

# 引数

  * `prob::XPRSprob`: 現在の問題。
  * `probname::Union{Nothing,AbstractString}`: 問題の名前を含む最大 `MAXPROBNAMELENGTH` 文字の文字列。
  * `ncols::Integer`: 行列の構造列の数。
  * `nrows::Integer`: 行列の行数（目的行を含まない）。
  * `rowtype::AbstractVector{Cchar}`: 行タイプを含む長さ `nrows` の文字配列: Lは `<=` 制約を示します（これを二次制約にも使用します）；Eは `=` 制約を示します；Gは `>=` 制約を示します；Rは範囲制約を示します；Nは非拘束制約を示します。
  * `rhs::AbstractVector{Number}`: 行の右辺係数を含む長さ `nrows` の倍精度配列。
  * `rng::AbstractVector{Number}`: 範囲行の範囲値を含む長さ `nrows` の倍精度配列。
  * `objcoef::AbstractVector{Number}`: 目的関数係数を含む長さ `ncols` の倍精度配列。
  * `start::AbstractVector{Integer}`: 各列の要素の開始位置を示す `rowind` および `rowcoef` 配列のオフセットを含む整数配列。
  * `collen::AbstractVector{Integer}`: 各列の非ゼロ要素の数を含む長さ `ncols` の整数配列。
  * `rowind::AbstractVector{Integer}`: 各列の非ゼロ要素の行インデックスを含む整数配列。
  * `rowcoef::AbstractVector{Number}`: 非ゼロ要素の値を含む倍精度配列；`rowind` と同じ長さ。
  * `lb::AbstractVector{Number}`: 列の下限を含む長さ `ncols` の倍精度配列。
  * `ub::AbstractVector{Number}`: 列の上限を含む長さ `ncols` の倍精度配列。
  * `nobjqcoefs::Integer`: 二次項の数。
  * `objqcol1::AbstractVector{Integer}`: 各二次項の最初の変数の列インデックスを含むサイズ `nobjqcoefs` の整数配列。
  * `objqcol2::AbstractVector{Integer}`: 各二次項の二番目の変数の列インデックスを含むサイズ `nobjqcoefs` の整数配列。
  * `objqcoef::AbstractVector{Number}`: 二次係数を含むサイズ `nobjqcoefs` の倍精度配列。
  * `nqrows::Integer`: 二次行列を含む行の数。
  * `qrowind::AbstractVector{Integer}`: 二次行列を含む行のインデックスを含むサイズ `nqrows` の整数配列。
  * `nrowqcoef::AbstractVector{Integer}`: 各二次制約行列の非ゼロの数を含むサイズ `nqrows` の整数配列。
  * `rowqcol1::AbstractVector{Integer}`: サイズ `nqcelem` の整数配列で、`nqcelem` は `nrowqcoef` の要素の合計（すなわち、すべての制約における二次行列要素の総数）に等しい。
  * `rowqcol2::AbstractVector{Integer}`: サイズ `nqcelem` の整数配列で、二次制約行列の二番目のインデックスを含む。
  * `rowqcoef::AbstractVector{Number}`: サイズ `nqcelem` の整数配列で、二次制約行列の係数を含む。

# 戻り値

  * `prob::XPRSprob`: 現在の問題。

C APIの対応する関数 [XPRSloadqcqp](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSloadqcqp.html) のドキュメントも参照してください。
