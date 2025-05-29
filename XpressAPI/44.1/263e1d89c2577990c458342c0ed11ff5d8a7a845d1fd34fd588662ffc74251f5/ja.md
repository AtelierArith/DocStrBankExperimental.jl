```
XPRSaddcols(prob, ncols, ncoefs, objcoef, start, rowind, rowcoef, lb, ub)::prob
```

オプティマイザーマトリックスに列を追加します。

# 引数

  * `prob::XPRSprob`: 現在の問題。
  * `ncols::Integer`: 新しい列の数。
  * `ncoefs::Integer`: 追加された列の新しい非ゼロの数。
  * `objcoef::AbstractVector{Number}`: 新しい列の目的関数係数を含む長さ `ncols` のダブル配列。
  * `start::AbstractVector{Integer}`: 各列の要素の開始位置に対する `rowind` および `rowcoef` 配列のオフセットを含む長さ `ncols` の整数配列。
  * `rowind::AbstractVector{Integer}`: 各列の要素に対する行インデックスを含む長さ `ncoefs` の整数配列。
  * `rowcoef::AbstractVector{Number}`: 要素の値を含む長さ `ncoefs` のダブル配列。
  * `lb::AbstractVector{Number}`: 追加された列の下限を含む長さ `ncols` のダブル配列。
  * `ub::AbstractVector{Number}`: 追加された列の上限を含む長さ `ncols` のダブル配列。

# 戻り値

  * `prob::XPRSprob`: 現在の問題。

C APIの対応する関数 [XPRSaddcols](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSaddcols.html) のドキュメントも参照してください。
