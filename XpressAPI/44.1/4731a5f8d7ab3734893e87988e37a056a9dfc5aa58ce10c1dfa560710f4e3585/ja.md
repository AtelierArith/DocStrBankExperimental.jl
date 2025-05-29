```
XPRSgetqrows(prob, rowind)::nrows, rowind
```

二次係数を持つ行のリストインデックスを返します。

# 引数

  * `prob::XPRSprob`: 現在の問題。
  * `rowind::Union{XPRSallocatable,AbstractVector{Int32}}`: 二次係数を持つ行のインデックスを返すために使用される長さ `*nrows` の配列。この引数に `XPRS_ALLOC` を渡すことで、関数が適切なサイズの配列を自動的に割り当てます。

# 戻り値

  * `nrows::Int32`: 行列内の二次制約の数を返すために使用されます。
  * `rowind::AbstractVector{Int32}`: 二次係数を持つ行のインデックスを返すために使用される長さ `*nrows` の配列。

C API の対応する関数 [XPRSgetqrows](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSgetqrows.html) のドキュメントも参照してください。
