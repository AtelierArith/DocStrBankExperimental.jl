```
gaussian([T=Float64], size::NTuple{N, Int};
    offset=CtrFT,
    sigma=1.0,
    dims=ntuple(+, N),
    scale=ScaUnit,
    weight=1,
    accumulator=sum)
```

A gaussian peak positioned at offset. Note that the gaussian is NOT normalized by its integral, but by its maximum. For a version with a normalized integral, see `normal`. List-mode is supported also for the argument sigma.  See the final example below which generates 60 Gaussians at random positions with random strengths and width along X and Y.

# Arguments:

  * `sigma`: the (standard deviation) width of the Gaussian. If a tuple is supplied, each entry is interpreted as the width along the correspondin dimension.
  * `offset`: the center position of the Gaussian. You can use a tuple or the indicators `CtrCorner`, `CtrEnd`, `CtrFT`, `CtrRFT` etc.
  * `scale`: the scale of the pixel. By default `ScaUnit` is assumed
  * `dims`: the dimensions over which to apply this function to.
  * `weight`: the strength of the result. Supports list-mode (see rr2 for documentation)
  * `accumulator`: the method used for superimposing list-mode data. Only applies in list-mode

```jldoctest
julia> gaussian((5,5))
5×5 IndexFunArray{Float64, 2, IndexFunArrays.var"#100#102"{Float64, Tuple{Float64, Float64}, Tuple{Float64, Float64}}}:
 0.0183156  0.082085  0.135335  0.082085  0.0183156
 0.082085   0.367879  0.606531  0.367879  0.082085
 0.135335   0.606531  1.0       0.606531  0.135335
 0.082085   0.367879  0.606531  0.367879  0.082085
 0.0183156  0.082085  0.135335  0.082085  0.0183156

julia> gaussian((6,6), sigma=5.0)
 6×6 IndexFunArray{Float64, 2, IndexFunArrays.var"#100#102"{Float64, Tuple{Float64, Float64}, Tuple{Float64, Float64}}}:
  0.165299  0.272532  0.367879  0.40657   0.367879  0.272532
  0.272532  0.449329  0.606531  0.67032   0.606531  0.449329
  0.367879  0.606531  0.818731  0.904837  0.818731  0.606531
  0.40657   0.67032   0.904837  1.0       0.904837  0.67032
  0.367879  0.606531  0.818731  0.904837  0.818731  0.606531
  0.272532  0.449329  0.606531  0.67032   0.606531  0.449329

julia> gaussian(Float32,(5,5),offset=CtrCorner)
  5×5 IndexFunArray{Float32, 2, IndexFunArrays.var"#100#102"{Float32, Tuple{Float64, Float64}, Tuple{Float32, Float32}}}:
   1.0          0.606531     0.135335    0.011109    0.000335463
   0.606531     0.367879     0.082085    0.00673795  0.000203468
   0.135335     0.082085     0.0183156   0.00150344  4.53999f-5
   0.011109     0.00673795   0.00150344  0.00012341  3.72665f-6
   0.000335463  0.000203468  4.53999f-5  3.72665f-6  1.12535f-7

julia> y = gaussian((100,100),offset = (100,100) .* rand(2,60), weight=rand(60), sigma=2.0 .*(0.3 .+rand(2,60)));

```

---

gaussian(arr::AbstractArray; offset=CtrFt, sigma=1.0, scaling=ScaUnit)

This is a wrapper for  `gaussian(eltype(arr), size(arr), sigma=sigma, scaling=scaling, offset=offset)`.
