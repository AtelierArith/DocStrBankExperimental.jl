```
XPRSaddrows64(prob, nrows, ncoefs, rowtype, rhs, rng, start, colind, rowcoef)::prob
```

オプティマイザーマトリックスに行を追加します。

# 引数

  * `prob::XPRSprob`: 現在の問題。
  * `nrows::Integer`: 新しい行の数。
  * `ncoefs::Integer`: 追加された行の新しい非ゼロの数。
  * `rowtype::AbstractVector{Cchar}`: 行のタイプを含む長さ nrows の文字配列: L は `<=` 行を示し; G は `>=` 行を示し; E は = 行を示します。
  * `rhs::AbstractVector{Number}`: 右辺要素を含む長さ `nrows` の倍精度配列。
  * `rng::AbstractVector{Number}`: 行範囲要素を含む長さ `nrows` の倍精度配列。
  * `start::AbstractVector{Integer}`: 各行の要素の開始位置における `colind` および `rowcoef` 配列のオフセットを含む長さ `nrows` の整数配列。
  * `colind::AbstractVector{Integer}`: 各行の要素に対する（連続した）列インデックスを含む長さ `ncoefs` の整数配列。
  * `rowcoef::AbstractVector{Number}`: （連続した）要素値を含む長さ `ncoefs` の倍精度配列。

# 戻り値

  * `prob::XPRSprob`: 現在の問題。

C API の対応する関数 [XPRSaddrows64](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSaddrows64.html) のドキュメントも参照してください。
