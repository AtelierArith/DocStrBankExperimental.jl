```
XPRSgetpresolvemap(prob, rowmap, colmap)::rowmap, colmap
```

元の問題に戻すためのプレソルブ問題からの行と列の番号のマッピングを返します。

# 引数

  * `prob::XPRSprob`: 現在の問題。
  * `rowmap::Union{XPRSallocatable,Nothing,AbstractVector{Int32}}`: 行マップが返される長さROWSの整数配列。適切なサイズの配列を関数が割り当てるようにするには、この引数に`XPRS_ALLOC`を渡すことができます。この引数に`nothing`を渡すと、その情報を照会しません。
  * `colmap::Union{XPRSallocatable,Nothing,AbstractVector{Int32}}`: 列マップが返される長さCOLSの整数配列。適切なサイズの配列を関数が割り当てるようにするには、この引数に`XPRS_ALLOC`を渡すことができます。この引数に`nothing`を渡すと、その情報を照会しません。

# 戻り値

  * `rowmap::Union{Nothing,AbstractVector{Int32}}`: 行マップが返される長さROWSの整数配列。
  * `colmap::Union{Nothing,AbstractVector{Int32}}`: 列マップが返される長さCOLSの整数配列。

C APIの対応する関数のドキュメント[XPRSgetpresolvemap](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSgetpresolvemap.html)も参照してください。
