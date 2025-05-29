```
FITS_pointer
```

オブジェクトは[`HDU_ptr`](@ref)オブジェクトの配列を保持します。

フィールドは次のとおりです：

  * `.nblock`     : ブロック数 (`::Int`)
  * `.nhdu`       : hdu数 (`::Int`)
  * `.block_start`: ブロック開始ポインタ: (`::Tuple(Vector{Int})`)
  * `.block_stop`: ブロック終了ポインタ: (`::Tuple(Vector{Int})`)
  * `.hdu_start`: hdu開始ポインタ: (`::Tuple(Vector{Int})`)
  * `.hdu_stop`: hdu終了ポインタ: (`::Tuple(Vector{Int})`)
  * `.hdr_start`: ヘッダー開始ポインタ: (`::Tuple(Vector{Int})`)
  * `.hdr_stop`: ヘッダー終了ポインタ: (`::Tuple(Vector{Int})`)
  * `.data_start`: データ開始ポインタ: (`::Tuple(Vector{Int})`)
  * `.data_stop`: データ終了ポインタ: (`::Tuple(Vector{Int})`)
