```
window_edge([T=Float64], size::NTuple; 
            offset=CtrFT, scale=ScaFTEdge, border_in=0.8, border_out=1.0, dims=ntuple(+, N))
```

境界（`border_out`）の半分で急激に遷移する多次元（分離可能）ウィンドウで、境界の内側は1（`border_in`）です。引数の詳細については`?window_linear`を参照してください。

---

```
window_edge(arr::AbstractArray; offset=CtrFt, scaling=ScaUnit,
                                  border_in=0.8, border_out=1.0)
```

これは、`window_edge(eltype(arr), size(arr), scaling=scaling, offset=offset, border_in=border_in, border_out=border_out)`のラッパーです。
