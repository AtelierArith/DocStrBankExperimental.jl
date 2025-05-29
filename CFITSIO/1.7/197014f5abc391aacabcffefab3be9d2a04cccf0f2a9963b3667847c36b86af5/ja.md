```
fits_write_subset(f::FITSFile,
                  fpixel::V, lpixel::V,
                  data::StridedArray) where {V<:Union{Vector{<:Integer}, Tuple{Vararg{Integer}}}}
```

FITS画像の長方形のセクションを書き込みます。書き込むピクセルの数は、最初と最後のピクセル（それぞれ`fpixel`および`lpixel`引数として指定）から計算されます。

!!! note
    書き出すセクションはメモリ内で連続している必要があるため、最後の次元を除くすべての次元は軸範囲全体をカバーしなければなりません。引数`fpixel`および`lpixel`はこれを考慮する必要があります。


参照: [`fits_write_pix`](@ref)
