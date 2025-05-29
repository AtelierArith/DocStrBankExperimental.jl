```
REC!(rec_out::AbstractArray, D::AbstractArray, rec_threshold::Float64, temp_excl::Int = 0)
```

ループ内で使用するためのメモリ効率の良いバージョンの `REC()`。`rec_out` は事前に割り当てられた出力であり、`init_REC()` で初期化する必要があります。
