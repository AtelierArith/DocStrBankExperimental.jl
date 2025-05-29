```
fits_read_pixnull(f::FITSFile,
                  fpixel::Union{Vector{<:Integer}, Tuple{Vararg{Integer}}},
                  nelements::Integer, data::StridedArray, nullarray::Array{UInt8})
```

FITSファイルから`fpixel`から始まる位置に`nelements`ピクセルを`data`に読み込みます。出力時に、`data`に対応するnull値がある`nullarray`のインデックスは`1`に設定されます。

!!! note
    `data`はメモリに連続して格納される必要があります。


参照: [`fits_read_pix`](@ref)
