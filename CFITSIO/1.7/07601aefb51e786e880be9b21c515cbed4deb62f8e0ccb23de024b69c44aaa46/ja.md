```
fits_write_pix(f::FITSFile,
               fpixel::Union{Vector{<:Integer}, Tuple{Vararg{Integer}}},
               nelements::Integer, data::StridedArray)
```

`data`から`fpixel`ピクセルから始めて、`nelements`ピクセルをFITSファイルに書き込みます。

!!! note
    `data`はメモリ内に連続して格納されている必要があります。


参照: [`fits_write_pixnull`](@ref)
