```
fits_read_subset(f::FITSFile,
                 fpixel::V, lpixel::V, inc::V,
                 [nulval],
                 data::StridedArray) where {V<:Union{Vector{<:Integer}, Tuple{Vararg{Integer}}}}
```

FITS画像の長方形のセクションを読み取ります。読み取るピクセルの数は、最初のピクセル（`fpixel`引数として指定）と最後のピクセル（`lpixel`引数として指定）から計算されます。引数`inc`は、各次元に沿ったピクセルのステップサイズを指定します。

オプションの引数`nulval`が指定され、かつゼロでない場合、`data`内のヌル値はそれに置き換えられます。

!!! note
    `data`はメモリ内に連続して格納される必要があり、読み取られたピクセルで連続的に埋められます。


関連情報: [`fits_read_pix`](@ref)
