```
window_blackman_harris([T=Float64], size::NTuple; 
                      offset=CtrFT, scale=ScaFTEdge, border_in=0.8, border_out=1.0, dims=ntuple(+, N))
```

ブラックマン/ハリスに従った境界（`border_out`）から1（`border_in`）への遷移を持つ多次元（分離可能）ウィンドウです。引数の詳細については `?window_linear` を参照してください。

---

```
window_blackman_harris(arr::AbstractArray;
                      offset=CtrFT, scale=ScaFTEdge, border_in=0.8, border_out=1.0, dims=ntuple(+, N))
```

これは `window_blackman_harris(eltype(arr), size(arr), scaling=scaling, offset=offset, border_in=border_in, border_out=border_out)` のラッパーです。
