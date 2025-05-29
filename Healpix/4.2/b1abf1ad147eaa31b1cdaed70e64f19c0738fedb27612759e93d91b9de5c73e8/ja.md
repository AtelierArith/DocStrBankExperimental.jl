```
writeClToFITS(f::CFITSIO.FITSFile, Cl::Vector{T}) where {T <: Real}
writeClToFITS(fileName, Cl::Vector{T}; overwrite = true) where {T <: Real}
```

C_ℓ係数のセットをFITSファイルに書き込みます。
