```
fits_read_pix(f::FITSFile,
              fpixel::NTuple{Vector{<:Integer}, Tuple{Vararg{Integer}}},
              nelements::Integer, [nulval], data::StridedArray)
```

FITSファイルから`fpixel`のピクセルから始めて`data`に`nelements`ピクセルを読み込みます。オプション引数`nulval`が指定され、かつゼロでない場合、配列内の任意のヌル値はそれに置き換えられます。

!!! note
    `data`はメモリ内に連続して格納されている必要があります。


参照: [`fits_read_pixnull`](@ref), [`fits_read_subset`](@ref)
