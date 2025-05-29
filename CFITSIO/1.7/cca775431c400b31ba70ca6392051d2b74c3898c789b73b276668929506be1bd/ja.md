```
fits_read_pixnull(f::FITSFile, data::StridedArray, nullarray::Array{UInt8})
```

FITSファイルから最初のピクセルから`data`に`length(data)`ピクセルを読み込みます。出力時に、`data`に対応するnull値がある`nullarray`のインデックスは`1`に設定されます。

!!! note
    `data`はメモリに連続して格納されている必要があります。


参照: [`fits_read_pix`](@ref)
