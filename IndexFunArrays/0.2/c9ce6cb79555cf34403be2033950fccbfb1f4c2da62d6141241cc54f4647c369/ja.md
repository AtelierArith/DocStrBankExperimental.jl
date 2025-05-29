```
window_radial_gaussian([T=Float64], size::NTuple; 
                      offset=CtrFT, scale=ScaFTEdge, border_in=0.8, border_out=1.0, dims=ntuple(+, N))
```

境界（`border_out`）から1（`border_in`）への間にガウス遷移を持つ多次元放射ウィンドウ。デフォルトでは、ガウスの標準偏差`sigma`は、`border_out`で`2 sigma`レベルに達するように調整されます。ただし、このウィンドウは外側の境界でクリップされないため、`border_out`を`border_in`に近づけることでsigmaを調整できます。`border_in`と`border_out`は`radial`タイプのウィンドウに対するスカラー値であることに注意してください。楕円率は`scale`パラメータを介して調整できます。引数の詳細については`?window_radial_linear`を参照してください。

---

window*radial*gaussian(arr::AbstractArray;                                   offset=CtrFT, scale=ScaFTEdge, border*in=0.8, border*out=1.0, dims=ntuple(+, N)) これは`window_radial_gaussian(eltype(arr), size(arr), scaling=scaling, offset=offset, border_in=border_in, border_out=border_out)`のラッパーです。
