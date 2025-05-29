```
fits_read_pix(f::FITSFile, data::StridedArray, [nulval])
```

FITSファイルから最初のピクセルから`data`に`length(data)`ピクセルを読み込みます。オプションの引数`nulval`は、指定されていて非ゼロの場合、配列内の任意のヌル値を置き換えるために使用されます。

!!! note
    `data`はメモリ内に連続して格納されている必要があります。


参照: [`fits_read_pixnull`](@ref)
