```
box([::Type{T}], size::NTuple, boxsize=size./2; offset=CtrFT, scale=ScaFTEdge, dims=ntuple(+, N))
```

多次元ボックスで、内部が1、外部が0です。`boxsize`はボックスの外側の寸法を定義します。配列とボックスのフーリエ空間の中心に対応する整数ピクセルのボックスサイズを取得するために、0.25ピクセルの追加オフセットが自動的に適用され、この次元に沿ってボックスピクセルはボックスサイズの半分以下であれば1になります。

```julia
julia> box((10,10),(3,6))
10×10 IndexFunArray{Float64, 2, IndexFunArrays.var"#g#182"{Float64, Tuple{Float64, Float64}, Tuple{Float64, Float64}, Int64}}:
 0.0  0.0  0.0  0.0  0.0  0.0  0.0  0.0  0.0  0.0
 0.0  0.0  0.0  0.0  0.0  0.0  0.0  0.0  0.0  0.0
 0.0  0.0  0.0  0.0  0.0  0.0  0.0  0.0  0.0  0.0
 0.0  0.0  0.0  0.0  0.0  0.0  0.0  0.0  0.0  0.0
 0.0  0.0  1.0  1.0  1.0  1.0  1.0  1.0  0.0  0.0
 0.0  0.0  1.0  1.0  1.0  1.0  1.0  1.0  0.0  0.0
 0.0  0.0  1.0  1.0  1.0  1.0  1.0  1.0  0.0  0.0
 0.0  0.0  0.0  0.0  0.0  0.0  0.0  0.0  0.0  0.0
 0.0  0.0  0.0  0.0  0.0  0.0  0.0  0.0  0.0  0.0
 0.0  0.0  0.0  0.0  0.0  0.0  0.0  0.0  0.0  0.0

 julia> box((7,8))
 7×8 IndexFunArray{Float64, 2, IndexFunArrays.var"#g#182"{Float64, Tuple{Float64, Float64}, Tuple{Float64, Float64}, Int64}}:
  0.0  0.0  0.0  0.0  0.0  0.0  0.0  0.0
  0.0  0.0  1.0  1.0  1.0  1.0  0.0  0.0
  0.0  0.0  1.0  1.0  1.0  1.0  0.0  0.0
  0.0  0.0  1.0  1.0  1.0  1.0  0.0  0.0
  0.0  0.0  1.0  1.0  1.0  1.0  0.0  0.0
  0.0  0.0  0.0  0.0  0.0  0.0  0.0  0.0
  0.0  0.0  0.0  0.0  0.0  0.0  0.0  0.0
```

---

box(arr::AbstractArray, boxsize; offset=CtrFT, scale=ScaUnit, dims=ntuple(+, N))  

これは `box(eltype(arr), size(arr), boxsize; scaling=scaling, offset=offset)` のラッパーです。
