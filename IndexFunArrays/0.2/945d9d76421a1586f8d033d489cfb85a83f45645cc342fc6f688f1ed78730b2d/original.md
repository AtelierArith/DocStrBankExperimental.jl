```
normal([T=Float64], size::NTuple{N, Int};
    offset=CtrFT,
    sigma=1.0,
    scale=ScaUnit,
    weight=1,
    accumulator=sum)
```

A gaussian peak positioned at offset. Note that this normal distribution (Gaussian) is normalized by its integral. For a version with normalized to the maximum, see `gaussian`.

# Arguments:

  * `sigma`: the (standard deviation) width of the Gaussian
  * `offset`: the center position of the Gaussian. You can use a tuple or the indicators `CtrCorner`, `CtrEnd`, `CtrFT`, `CtrRFT` etc.
  * `scale`: the scale of the pixel. By default `ScaUnit` is assumed
  * `weight`: the strength of the result. Supports list-mode (see rr2 for documentation)
  * `accumulator`: the method used for superimposing list-mode data. Only applies in list-mode

```jldoctest
julia> normal((5,5))
5×5 IndexFunArray{Float64, 2, IndexFunArrays.var"#107#109"{Float64, Tuple{Float64, Float64}, Tuple{Float64, Float64}}}:
 0.00291502  0.0130642  0.0215393  0.0130642  0.00291502
 0.0130642   0.0585498  0.0965324  0.0585498  0.0130642
 0.0215393   0.0965324  0.159155   0.0965324  0.0215393
 0.0130642   0.0585498  0.0965324  0.0585498  0.0130642
 0.00291502  0.0130642  0.0215393  0.0130642  0.00291502

julia> sum(normal((5,5)))
 0.9818147610543744

julia> sum(normal((25,25)))
 1.000000010701151

julia> sum(normal((55,55), sigma=(5.0,2.0)))
0.9999999639340563
```

---

normal(arr::AbstractArray; offset=CtrFt, sigma=1.0, scaling=ScaUnit)

This is a wrapper for  `normal(eltype(arr), size(arr), sigma=sigma, scaling=scaling, offset=offset)`.
