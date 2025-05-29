```
XPRSgetcoltype(prob, coltype, first, last)::coltype
```

指定された範囲内の列のタイプを返します。

# 引数

  * `prob::XPRSprob`: 現在の問題。
  * `coltype::Union{XPRSallocatable,AbstractVector{Cchar}}`: 列のタイプが返される長さ `last-first+1` の文字配列: Cは連続変数を示し; Iは整数変数を示し; Bはバイナリ変数を示し; Sは半連続変数を示し; Rは半連続整数変数を示し; Pは部分整数変数を示します。この引数に `XPRS_ALLOC` を渡すことで、関数が適切なサイズの配列を自動的に割り当てます。
  * `first::Integer`: 範囲内の最初の列。
  * `last::Integer`: 範囲内の最後の列。

# 戻り値

  * `coltype::AbstractVector{Cchar}`: 列のタイプが返される長さ `last-first+1` の文字配列: Cは連続変数を示し; Iは整数変数を示し; Bはバイナリ変数を示し; Sは半連続変数を示し; Rは半連続整数変数を示し; Pは部分整数変数を示します。

C APIの対応する関数 [XPRSgetcoltype](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSgetcoltype.html) のドキュメントも参照してください。
