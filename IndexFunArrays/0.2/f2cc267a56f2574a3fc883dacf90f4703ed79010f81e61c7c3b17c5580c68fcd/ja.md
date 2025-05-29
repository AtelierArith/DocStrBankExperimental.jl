```
phiphi([T=Float64], size::NTuple{N, Int};
    offset=CtrFT,
    dims=ntuple(+, N),
    scale=ScaUnit,
    weight=1,
    accumulator=sum)
```

atan()を使用した方位スパイラル位相ランプ。方位位相は次元1と2にまたがります。すべてのオプションの説明については`rr2`を参照してください。

```jldoctest
julia> phiphi((5, 5))
5×5 IndexFunArray{Float64, 2, IndexFunArrays.var"#29#30"{Float64, Tuple{Float64, Float64}, Tuple{Int64, Int64}}}:
 -2.35619   -2.67795   3.14159  2.67795   2.35619
 -2.03444   -2.35619   3.14159  2.35619   2.03444
 -1.5708    -1.5708    0.0      1.5708    1.5708
 -1.10715   -0.785398  0.0      0.785398  1.10715
 -0.785398  -0.463648  0.0      0.463648  0.785398
```

---

```
phiphi(arr::AbstractArray; offset=CtrFt, scaling=ScaUnit)
```

これは `phiphi(eltype(arr), size(arr), scaling=scaling, offset=offset)` のラッパーです。
