```
readClFromFITS{T <: Real}(f::CFITSIO.FITSFile, t::Type{T}; col_num = 2) -> Vector{T}
readClFromFITS{T <: Real}(fileName::String, t::Type{T}; col_num = 2) -> Vector{T}
```

FITSファイルからC_ℓ係数のセットを読み取ります。
