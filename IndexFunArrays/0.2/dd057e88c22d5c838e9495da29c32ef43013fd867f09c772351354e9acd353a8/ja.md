```
window_radial_hanning([T=Float64], size::NTuple; 
                   offset=CtrFT, scale=ScaFTEdge, border_in=0.8, border_out=1.0, dims=ntuple(+, N))
```

境界（`border_out`）から1（`border_in`）への間にvon Hann遷移を持つ多次元放射ウィンドウ。`border_in`と`border_out`は`radial`タイプのウィンドウに対してスカラー値である必要があることに注意してください。楕円率は`scale`パラメータを介して調整できます。引数の詳細については`?window_radial_linear`を参照してください。

---

```
window_radial_hanning(arr::AbstractArray;
                      offset=CtrFT, scale=ScaFTEdge, border_in=0.8, border_out=1.0, dims=ntuple(+, N))
```

これは`window_radial_hanning(eltype(arr), size(arr), scaling=scaling, offset=offset, border_in=border_in, border_out=border_out)`のラッパーです。
