```
XPRSgetmipentities64(prob, coltype, colind, limit, settype, start, setcols, refval)::nentities, nsets, coltype, colind, limit, settype, start, setcols, refval
```

問題に関する整数およびエンティティ情報を取得します。

この関数は、プレスolveオプションが使用されている場合、XPRSmipoptimizeの前に呼び出す必要があります。

# 引数

  * `prob::XPRSprob`: 現在の問題。
  * `coltype::Union{XPRSallocatable,Nothing,AbstractVector{Cchar}}`: エンティティタイプが返される長さ `nentities` の文字配列。この引数に `XPRS_ALLOC` を渡すことで、関数が適切なサイズの配列を自動的に割り当てます。この引数に `nothing` を渡すことで、その情報を照会しないことができます。
  * `colind::Union{XPRSallocatable,Nothing,AbstractVector{Int32}}`: MIPエンティティの列インデックスが返される長さ `nentities` の整数配列。この引数に `XPRS_ALLOC` を渡すことで、関数が適切なサイズの配列を自動的に割り当てます。この引数に `nothing` を渡すことで、その情報を照会しないことができます。
  * `limit::Union{XPRSallocatable,Nothing,AbstractVector{Float64}}`: 部分整数変数の制限および半連続および半連続整数変数の下限が返される長さ `nentities` の倍精度配列（バイナリおよび整数変数に対応する位置のエントリは無意味になります）。この引数に `XPRS_ALLOC` を渡すことで、関数が適切なサイズの配列を自動的に割り当てます。この引数に `nothing` を渡すことで、その情報を照会しないことができます。
  * `settype::Union{XPRSallocatable,Nothing,AbstractVector{Cchar}}`: セットタイプが返される長さ `nsets` の文字配列。この引数に `XPRS_ALLOC` を渡すことで、関数が適切なサイズの配列を自動的に割り当てます。この引数に `nothing` を渡すことで、その情報を照会しないことができます。
  * `start::AbstractVector{Int64}`: `setcols` および `refval` 配列へのオフセットを示す整数配列で、セットの開始位置が返されます。
  * `setcols::AbstractVector{Int32}`: 各セットの列が返される長さ `SETMEMBERS` の整数配列。
  * `refval::AbstractVector{Float64}`: 各セットのメンバーの参照行エントリが返される長さ `SETMEMBERS` の倍精度配列。

# 戻り値

  * `nentities::Int32`: バイナリ、整数、半連続、半連続整数および部分整数エンティティの数が返される整数へのポインタ。
  * `nsets::Int32`: SOS1およびSOS2セットの数が返される整数へのポインタ。
  * `coltype::Union{Nothing,AbstractVector{Cchar}}`: エンティティタイプが返される長さ `nentities` の文字配列。
  * `colind::Union{Nothing,AbstractVector{Int32}}`: MIPエンティティの列インデックスが返される長さ `nentities` の整数配列。
  * `limit::Union{Nothing,AbstractVector{Float64}}`: 部分整数変数の制限および半連続および半連続整数変数の下限が返される長さ `nentities` の倍精度配列（バイナリおよび整数変数に対応する位置のエントリは無意味になります）。
  * `settype::Union{Nothing,AbstractVector{Cchar}}`: セットタイプが返される長さ `nsets` の文字配列。
  * `start::AbstractVector{Int64}`: `setcols` および `refval` 配列へのオフセットを示す整数配列で、セットの開始位置が返されます。
  * `setcols::AbstractVector{Int32}`: 各セットの列が返される長さ `SETMEMBERS` の整数配列。
  * `refval::AbstractVector{Float64}`: 各セットのメンバーの参照行エントリが返される長さ `SETMEMBERS` の倍精度配列。

対応する関数のドキュメント [XPRSgetmipentities64](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSgetmipentities64.html) をC APIで参照してください。
