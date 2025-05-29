```
window_radial_linear([T=Float64], size::NTuple; 
            offset=CtrFT, scale=ScaFTEdge, border_in=0.8, border_out=1.0, dims=ntuple(+, N))
```

境界（`border_out`）でゼロから（`border_in`）で1への線形遷移を持つ多次元放射ウィンドウ。`border_in` と `border_out` は `radial` タイプのウィンドウに対してスカラー値である必要があることに注意してください。楕円率は `scale` パラメータを介して調整できます。デフォルトのオフセットとスケールでは、境界はエッジに対して相対的に指定されます。

```jldoctest
julia> window_radial_linear((4,5),border_in=0.0)
4×5 IndexFunArray{Float64, 2, IndexFunArrays.var"#59#60"{Float64, Tuple{Float64, Float64}, Tuple{Float64, Float64}, Float64, Float64}}:
 0.0  0.0       0.0  0.0       0.0
 0.0  0.292893  0.5  0.292893  0.0
 0.0  0.5       1.0  0.5       0.0
 0.0  0.292893  0.5  0.292893  0.0
```

---

```
window_radial_linear(arr::AbstractArray; offset=CtrFt, scaling=ScaUnit,
                     border_in=0.8, border_out=1.0, dims=ntuple(+, N))
```

これは `window_radial_linear(eltype(arr), size(arr), scaling=scaling, offset=offset, border_in=border_in, border_out=border_out)` のラッパーです。
