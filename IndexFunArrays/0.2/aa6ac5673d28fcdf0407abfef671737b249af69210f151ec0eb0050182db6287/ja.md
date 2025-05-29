```
disc([::Type{T}], size::NTuple, disc_radius; offset=CtrFT, scale=ScaFTEdge, dims=ntuple(+, N))
```

多次元ディスク（すなわち、2Dの円盤および3Dの充填球）であり、内部が1、外部が0です。`disc_radius`はディスクの半径を定義します。デフォルトの結果データ型はFloat64です。ディスクを生成する代替手段としてエッジウィンドウがあります。

```jldoctest
julia> disc((10,10),(3,5))
10×10 IndexFunArray{Float64, 2, IndexFunArrays.var"#g#194"{Float64, Tuple{Int64, Int64}, Tuple{Float64, Float64}, Int64}}:
 0.0  0.0  0.0  0.0  0.0  0.0  0.0  0.0  0.0  0.0
 0.0  0.0  0.0  0.0  0.0  0.0  0.0  0.0  0.0  0.0
 0.0  0.0  0.0  0.0  0.0  1.0  0.0  0.0  0.0  0.0
 0.0  0.0  1.0  1.0  1.0  1.0  1.0  1.0  1.0  0.0
 0.0  1.0  1.0  1.0  1.0  1.0  1.0  1.0  1.0  1.0
 1.0  1.0  1.0  1.0  1.0  1.0  1.0  1.0  1.0  1.0
 0.0  1.0  1.0  1.0  1.0  1.0  1.0  1.0  1.0  1.0
 0.0  0.0  1.0  1.0  1.0  1.0  1.0  1.0  1.0  0.0
 0.0  0.0  0.0  0.0  0.0  1.0  0.0  0.0  0.0  0.0
 0.0  0.0  0.0  0.0  0.0  0.0  0.0  0.0  0.0  0.0

 julia> disc((11,8),(0.5,0.5),scale=ScaFT)
11×8 IndexFunArray{Float64, 2, IndexFunArrays.var"#g#194"{Float64, Tuple{Int64, Int64}, Tuple{Float64, Float64}, Int64}}:
 0.0  0.0  0.0  1.0  1.0  1.0  0.0  0.0
 0.0  0.0  1.0  1.0  1.0  1.0  1.0  0.0
 0.0  1.0  1.0  1.0  1.0  1.0  1.0  1.0
 0.0  1.0  1.0  1.0  1.0  1.0  1.0  1.0
 0.0  1.0  1.0  1.0  1.0  1.0  1.0  1.0
 1.0  1.0  1.0  1.0  1.0  1.0  1.0  1.0
 0.0  1.0  1.0  1.0  1.0  1.0  1.0  1.0
 0.0  1.0  1.0  1.0  1.0  1.0  1.0  1.0
 0.0  1.0  1.0  1.0  1.0  1.0  1.0  1.0
 0.0  0.0  1.0  1.0  1.0  1.0  1.0  0.0
 0.0  0.0  0.0  1.0  1.0  1.0  0.0  0.0
```

---

disc(arr::AbstractArray, disc_radius; offset=CtrFT, scale=ScaUnit, dims=ntuple(+, N))  

これは `disc(eltype(arr), size(arr), disc_radius; scaling=scaling, offset=offset)` のラッパーです。
