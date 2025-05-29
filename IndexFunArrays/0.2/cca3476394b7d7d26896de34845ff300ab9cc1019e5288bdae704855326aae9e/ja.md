```
window_gaussian([T=Float64], size::NTuple; 
                      offset=CtrFT, scale=ScaFTEdge, border_in=0.8, border_out=1.0, dims=ntuple(+, N))
```

境界（`border_out`）から1（`border_in`）までの間に減衰するガウス関数に従った多次元（分離可能）ウィンドウです。デフォルトでは、ガウス関数の標準偏差`sigma`は、`border_out`で`2 sigma`レベルに達するように調整されます。ただし、このウィンドウは外側の境界でクリップされないため、`border_out`を`border_in`に近づけることで`sigma`を調整できます。引数の詳細については`?window_linear`を参照してください。

```jldoctest
julia> w1 = window_gaussian((9,9), border_in=(0.3,0.3), border_out=(0.6,1))
9×9 IndexFunArray{Float64, 2, IndexFunArrays.var"#286#288"{Float64, Tuple{Float64, Float64}, Tuple{Float64, Float64}, Tuple{Float64, Float64}, Tuple{Float64, Int64}}}:
 0.000109245  0.000259904  0.000413188  0.000449917  0.000449917  0.000449917  0.000413188  0.000259904  0.000109245
 0.012239     0.0291178    0.0462907    0.0504055    0.0504055    0.0504055    0.0462907    0.0291178    0.012239
 0.152725     0.363345     0.577637     0.628984     0.628984     0.628984     0.577637     0.363345     0.152725
 0.242811     0.57767      0.918365     1.0          1.0          1.0          0.918365     0.57767      0.242811
 0.242811     0.57767      0.918365     1.0          1.0          1.0          0.918365     0.57767      0.242811
 0.242811     0.57767      0.918365     1.0          1.0          1.0          0.918365     0.57767      0.242811
 0.152725     0.363345     0.577637     0.628984     0.628984     0.628984     0.577637     0.363345     0.152725
 0.012239     0.0291178    0.0462907    0.0504055    0.0504055    0.0504055    0.0462907    0.0291178    0.012239
 0.000109245  0.000259904  0.000413188  0.000449917  0.000449917  0.000449917  0.000413188  0.000259904  0.000109245
```

---

```
window_gaussian(arr::AbstractArray;
                      offset=CtrFT, scale=ScaFTEdge, border_in=0.8, border_out=1.0, dims=ntuple(+, N))
```

これは`window_gaussian(eltype(arr), size(arr), scaling=scaling, offset=offset, border_in=border_in, border_out=border_out)`のラッパーです。
