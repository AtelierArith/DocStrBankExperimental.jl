```
XPRSgetiisdata(prob, iis, rowind, colind, contype, bndtype, duals, djs, isolationrows, isolationcols)::nrows, ncols, rowind, colind, contype, bndtype, duals, djs, isolationrows, isolationcols
```

不減少不適合集合に関する情報を返します：サイズ、変数および制約（行および列ベクトル）、および変数の対立する側。

純粋な線形問題の場合、双対、削減コスト、および孤立に関する情報もあります。

# 引数

  * `prob::XPRSprob`: 現在の問題。
  * `iis::Integer`: データを取得するIISの序数。
  * `rowind::Union{XPRSallocatable,Nothing,AbstractVector{Int32}}`: IIS内の行のインデックス。適切なサイズの配列を関数に割り当てさせるために、この引数に`XPRS_ALLOC`を渡すことができます。この引数に`nothing`を渡すと、その情報を照会しません。
  * `colind::Union{XPRSallocatable,Nothing,AbstractVector{Int32}}`: IIS内の境界（列）のインデックス。適切なサイズの配列を関数に割り当てさせるために、この引数に`XPRS_ALLOC`を渡すことができます。この引数に`nothing`を渡すと、その情報を照会しません。
  * `contype::Union{XPRSallocatable,Nothing,AbstractVector{Cchar}}`: IIS内の行の感覚：Lは小さいか等しい行; Gは大きいか等しい行。適切なサイズの配列を関数に割り当てさせるために、この引数に`XPRS_ALLOC`を渡すことができます。この引数に`nothing`を渡すと、その情報を照会しません。
  * `bndtype::Union{XPRSallocatable,Nothing,AbstractVector{Cchar}}`: IIS内の境界の感覚：Uは上限; Lは下限。適切なサイズの配列を関数に割り当てさせるために、この引数に`XPRS_ALLOC`を渡すことができます。この引数に`nothing`を渡すと、その情報を照会しません。
  * `duals::Union{XPRSallocatable,Nothing,AbstractVector{Float64}}`: 行に関連付けられた双対乗数。適切なサイズの配列を関数に割り当てさせるために、この引数に`XPRS_ALLOC`を渡すことができます。この引数に`nothing`を渡すと、その情報を照会しません。
  * `djs::Union{XPRSallocatable,Nothing,AbstractVector{Float64}}`: 境界に関連付けられた双対乗数（削減コスト）。適切なサイズの配列を関数に割り当てさせるために、この引数に`XPRS_ALLOC`を渡すことができます。この引数に`nothing`を渡すと、その情報を照会しません。
  * `isolationrows::Union{XPRSallocatable,Nothing,AbstractVector{Cchar}}`: 行の孤立状態：-1は行の孤立情報が利用できない（iis孤立を実行）；0は行が孤立していない；1は行が孤立している。適切なサイズの配列を関数に割り当てさせるために、この引数に`XPRS_ALLOC`を渡すことができます。この引数に`nothing`を渡すと、その情報を照会しません。
  * `isolationcols::Union{XPRSallocatable,Nothing,AbstractVector{Cchar}}`: 境界の孤立状態：-1は列の孤立情報が利用できない（iis孤立を実行）；0は列が孤立していない；1は列が孤立している。適切なサイズの配列を関数に割り当てさせるために、この引数に`XPRS_ALLOC`を渡すことができます。この引数に`nothing`を渡すと、その情報を照会しません。

# 戻り値

  * `nrows::Int32`: IIS内の行数が返される整数へのポインタ。
  * `ncols::Int32`: IIS内の境界数が返される整数へのポインタ。
  * `rowind::Union{Nothing,AbstractVector{Int32}}`: IIS内の行のインデックス。
  * `colind::Union{Nothing,AbstractVector{Int32}}`: IIS内の境界（列）のインデックス。
  * `contype::Union{Nothing,AbstractVector{Cchar}}`: IIS内の行の感覚：Lは小さいか等しい行; Gは大きいか等しい行。
  * `bndtype::Union{Nothing,AbstractVector{Cchar}}`: IIS内の境界の感覚：Uは上限; Lは下限。
  * `duals::Union{Nothing,AbstractVector{Float64}}`: 行に関連付けられた双対乗数。
  * `djs::Union{Nothing,AbstractVector{Float64}}`: 境界に関連付けられた双対乗数（削減コスト）。
  * `isolationrows::Union{Nothing,AbstractVector{Cchar}}`: 行の孤立状態：-1は行の孤立情報が利用できない（iis孤立を実行）；0は行が孤立していない；1は行が孤立している。
  * `isolationcols::Union{Nothing,AbstractVector{Cchar}}`: 境界の孤立状態：-1は列の孤立情報が利用できない（iis孤立を実行）；0は列が孤立していない；1は列が孤立している。

対応する関数のドキュメント[XPRSgetiisdata](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSgetiisdata.html)も参照してください。
