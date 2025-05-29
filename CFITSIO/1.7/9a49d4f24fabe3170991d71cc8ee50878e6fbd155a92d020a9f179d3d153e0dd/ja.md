```
fits_write_pixnull(f::FITSFile,
                   fpixel::Union{Vector{<:Integer}, Tuple{Vararg{Integer}}},
                   nelements::Integer, data::StridedArray, nulval)
```

`nelements` ピクセルを `data` から FITS ファイルに書き込み、ピクセル `fpixel` から開始します。引数 `nulval` は「ヌル値」と見なされる値を指定し、`data` の要素型に対応する適切な数値に置き換えられます。

!!! note
    `data` はメモリ内に連続して格納されている必要があります。


参照: [`fits_write_pix`](@ref)
