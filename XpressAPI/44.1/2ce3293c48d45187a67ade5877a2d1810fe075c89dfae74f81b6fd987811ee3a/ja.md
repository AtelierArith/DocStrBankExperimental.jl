```
XPRS_bo_getrows(bo, branch, maxrows, maxcoefs, rowtype, rhs, start, colind, rowcoef)::nrows, ncoefs, rowtype, rhs, start, colind, rowcoef
```

ユーザーブランチオブジェクトのブランチに対する制約を返します。

# 引数

  * `bo::XPRSbranchobject`: 検査するユーザーブランチオブジェクト。
  * `branch::Integer`: 制約を取得するブランチの番号。
  * `maxrows::Integer`: 返す最大行数。
  * `maxcoefs::Integer`: 返す最大非ゼロ係数の数。
  * `rowtype::Union{XPRSallocatable,Nothing,AbstractVector{Cchar}}`: 行のタイプが返される長さ `maxrows` の文字配列。適切なサイズの配列を関数に割り当てさせるために、この引数に `XPRS_ALLOC` を渡すことができます。この情報を照会しないために `nothing` を渡すこともできます。
  * `rhs::Union{XPRSallocatable,Nothing,AbstractVector{Float64}}`: 右辺の値が返される長さ `maxrows` の倍精度配列。適切なサイズの配列を関数に割り当てさせるために、この引数に `XPRS_ALLOC` を渡すことができます。この情報を照会しないために `nothing` を渡すこともできます。
  * `start::Union{XPRSallocatable,Nothing,AbstractVector{Int32}}`: 返される制約の非ゼロ係数の開始位置における `colind` および `rowcoef` 配列のオフセットで埋められる長さ `maxrows` の整数配列。適切なサイズの配列を関数に割り当てさせるために、この引数に `XPRS_ALLOC` を渡すことができます。この情報を照会しないために `nothing` を渡すこともできます。
  * `colind::Union{XPRSallocatable,Nothing,AbstractVector{Int32}}`: 非ゼロ係数の列インデックスで埋められる長さ `maxcoefs` の整数配列。適切なサイズの配列を関数に割り当てさせるために、この引数に `XPRS_ALLOC` を渡すことができます。この情報を照会しないために `nothing` を渡すこともできます。
  * `rowcoef::Union{XPRSallocatable,Nothing,AbstractVector{Float64}}`: 非ゼロ係数の値で埋められる長さ `maxcoefs` の倍精度配列。適切なサイズの配列を関数に割り当てさせるために、この引数に `XPRS_ALLOC` を渡すことができます。この情報を照会しないために `nothing` を渡すこともできます。

# 戻り値

  * `nrows::Int32`: 行数が返されるメモリ位置。
  * `ncoefs::Int32`: 制約内の非ゼロ係数の数が返されるメモリ位置。
  * `rowtype::Union{Nothing,AbstractVector{Cchar}}`: 行のタイプが返される長さ `maxrows` の文字配列。
  * `rhs::Union{Nothing,AbstractVector{Float64}}`: 右辺の値が返される長さ `maxrows` の倍精度配列。
  * `start::Union{Nothing,AbstractVector{Int32}}`: 返される制約の非ゼロ係数の開始位置における `colind` および `rowcoef` 配列のオフセットで埋められる長さ `maxrows` の整数配列。
  * `colind::Union{Nothing,AbstractVector{Int32}}`: 非ゼロ係数の列インデックスで埋められる長さ `maxcoefs` の整数配列。
  * `rowcoef::Union{Nothing,AbstractVector{Float64}}`: 非ゼロ係数の値で埋められる長さ `maxcoefs` の倍精度配列。

C APIの対応する関数のドキュメント [XPRS*bo*getrows](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRS_bo_getrows.html) も参照してください。
