```
XPRSpresolverow(prob, rowtype, norigcoefs, origcolind, origrowcoef, origrhs, maxcoefs, colind, rowcoef)::ncoefs, colind, rowcoef, rhs, status
```

元の変数に基づいて定式化された行を前処理し、前処理された行列に追加できるようにします。

# 引数

  * `prob::XPRSprob`: 現在の問題。
  * `rowtype::Integer`: 行のタイプ：Lは `<=` 行を示し、Gは `>=` 行を示します。
  * `norigcoefs::Integer`: `origcolind` および `origrowcoef` 配列の要素数。
  * `origcolind::AbstractVector{Integer}`: 前処理する行の列インデックスを含む長さ `norigcoefs` の整数配列。
  * `origrowcoef::AbstractVector{Number}`: 前処理する行の非ゼロ係数を含む長さ `norigcoefs` の倍精度配列。
  * `origrhs::Float64`: 前処理する行の右辺定数。
  * `maxcoefs::Integer`: `colind` および `rowcoef` 配列に返す最大要素数。
  * `colind::Union{XPRSallocatable,Nothing,AbstractVector{Int32}}`: 前処理された行の列インデックスで埋められる整数配列。この引数に `XPRS_ALLOC` を渡すと、関数が適切なサイズの配列を自動的に割り当てます。この引数に `nothing` を渡すと、その情報を照会しません。
  * `rowcoef::Union{XPRSallocatable,Nothing,AbstractVector{Float64}}`: 前処理された行の係数で埋められる倍精度配列。この引数に `XPRS_ALLOC` を渡すと、関数が適切なサイズの配列を自動的に割り当てます。この引数に `nothing` を渡すと、その情報を照会しません。

# 戻り値

  * `ncoefs::Int32`: `colind` および `rowcoef` 配列の要素数が返される整数へのポインタ。
  * `colind::Union{Nothing,AbstractVector{Int32}}`: 前処理された行の列インデックスで埋められる整数配列。
  * `rowcoef::Union{Nothing,AbstractVector{Float64}}`: 前処理された行の係数で埋められる倍精度配列。
  * `rhs::Float64`: 前処理された右辺が返される倍精度へのポインタ。
  * `status::Int32`: 前処理された行のステータス： -3 行の前処理に失敗しました（前処理の双対削減による）； -2 行の前処理に失敗しました（前処理の重複列削減による）； -1 行の前処理に失敗しました（エラーによる）。

C APIの対応する関数 [XPRSpresolverow](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSpresolverow.html) のドキュメントも参照してください。
