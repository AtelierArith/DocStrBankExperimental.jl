```
exp_ikx([T=Float64], size::NTuple{N, Int};
    offset=CtrFT,
    shift_by=size.÷2
    dims=ntuple(+, N),
    scale=ScaFT,
    weight=1,
    accumulator=sum)
```

A complex-valued phase ramp according to `exp(-2pi i <k,x>)`. If applied as a multiplicative factor in Fourier space, it will lead to a shift of `x` pixels in real space. Note that this effect is actually realized by a change to the scaling parameter. The default shift is `size.÷2` which corresponds to `CtrFT`, however, the Ctr... arguments cannot be used for `shift_by`.

The argument `shift_by` supports list-mode, which can be used to conveniently perform multiple shifts simulatneously. See the final example below, which generates delta peaks at randomized subpixel positions.

# Arguments:

  * `offset`: the center position of the Gaussian. You can use a tuple or the indicators `CtrCorner`, `CtrEnd`, `CtrFT`, `CtrRFT` etc.
  * `shift_by`: the amount to shift by in real space.
  * `scale`: the scale of the pixel. By default `ScaUnit` is assumed
  * `dims`: the dimensions over which to apply this function to.
  * `weight`: the strength of the result. Supports list-mode (see rr2 for documentation)
  * `accumulator`: the method used for superimposing list-mode data. Only applies in list-mode

```jldoctest
julia> a = rr((4,3),offset=CtrCorner)
4×3 IndexFunArray{Float64, 2, IndexFunArrays.var"#37#39"{Float64, Tuple{Float64, Float64}, Tuple{Int64, Int64}}}:
 0.0  1.0      2.0
 1.0  1.41421  2.23607
 2.0  2.23607  2.82843
 3.0  3.16228  3.60555

julia> using FourierTools; real(iffts(ffts(a).*exp_ikx(a, shift_by=(2.0,1.0))))
4×3 Matrix{Float64}:
 2.82843   2.0          2.23607
 3.60555   3.0          3.16228
 2.0      -2.22045e-16  1.0
 2.23607   1.0          1.41421

 julia> using FourierTools; y = real(ift(exp_ikx((101,101),weight=rand(60), shift_by=101.0 .*rand(2,60))));

```

---

```
exp_ikx(arr::AbstractArray; offset=CtrFt, shift_by==size(arr).÷2, scaling=ScaUnit)
```

This is a wrapper for  `exp_ikx(eltype(arr), size(arr), shift_by=shift_by, scaling=scaling, offset=offset)`.
