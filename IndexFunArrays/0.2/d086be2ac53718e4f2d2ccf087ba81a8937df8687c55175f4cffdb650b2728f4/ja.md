```
window_hanning([T=Float64], size::NTuple; 
                   offset=CtrFT, scale=ScaFTEdge, border_in=0.8, border_out=1.0, dims=ntuple(+, N))
```

境界（`border_out`）から1（`border_in`）への間にvon Hann遷移を持つ多次元（分離可能）ウィンドウです。引数の詳細については`?window_linear`を参照してください。

---

```
window_hanning(arr::AbstractArray;
                   offset=CtrFT, scale=ScaFTEdge, border_in=0.8, border_out=1.0, dims=ntuple(+, N))
```

これは`window_hanning(eltype(arr), size(arr), scaling=scaling, offset=offset, border_in=border_in, border_out=border_out)`のラッパーです。
