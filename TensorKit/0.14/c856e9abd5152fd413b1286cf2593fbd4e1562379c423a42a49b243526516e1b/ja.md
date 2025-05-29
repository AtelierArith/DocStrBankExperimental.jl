```
randisometry([::Type{T}=Float64], dims::Dims{2}) -> Array{T,2}
randhaar([::Type{T}=Float64], dims::Dims{2}) -> Array{T,2}
```

サイズ `dims` のランダムな等距離写像を作成し、Haar測度に従って一様に分布させます。

[`randuniform`](@ref) および [`randnormal`](@ref) も参照してください。
