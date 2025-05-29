```
propagator(size::NTuple{N, Int}; Δz=1.0, shift_by=(0,0), k_max=0.5, offset=CtrFT, scale=ScaFT, dims=ntuple(+, N), accumulator=sum, weight=1) where {N,T}

A complex-valued phase which describes the `k_z= Δz * sqrt(1-k_x^2-k_y^2)` phase change upon free space propagation. 

The argument `shift_by` and `Δz` arguments support list-mode, which can be used to conveniently perform multiple shifts simulatneously.

# Arguments:
* `offset`: the center position of the Gaussian. You can use a tuple or the indicators `CtrCorner`, `CtrEnd`, `CtrFT`, `CtrRFT` etc.
* `Δz`: the amount to propagate along the third dimension z by in real space in units (i.e. multiples) of the wavelength in the medium (`λ = n*λ₀`).  
* `shift_by`: the amount to shift by in x and y spatial direct in real space.
* `k_max`: indicates the sampling relative to the Nyquist frequency. In optics this should be `pixelpitch./λ` with the `pixelpitch` as a tuple and the wavelength `λ = n*λ₀` in the medium.
* `scale`: the scale of the pixel. By default `ScaUnit` is assumed
* `dims`: the dimensions over which to apply this function to.
* `weight`: the strength of the result. Supports list-mode (see rr2 for documentation)
* `accumulator`: the method used for superimposing list-mode data. Only applies in list-mode
```

## See also: `phase_kz()`

Example of a 2d propagator for refractive index of 1.0 and a vaccum wavelength `λ` of 500nm with a `sampling` of 250 nm in all three dimensions of space. The last line shows how to obtain a stack of 2D propagators, each for a different z-plane with uniform `sampling` along z being `sampling[3]`. Note that `propagator()` does not need to know about the wavelength or refractive index since its inputs are specified as multiples of the wavelength. Note also that this example just about fulfils Nyquist sampling for the resulting amplitude but would undersample intensity by a factor of two. For `propagator` the full numerical aperture (NA) is assumed and the user has to care for possible NA limitations. See the `PointSpreadFunctions.jl` package for more details.

```jldoctest
julia> using IndexFunArrays

julia> sz = (150,100,100); n=1.0; λ=0.500; sampling=(0.250, 0.250, 0.250);     

julia> prop = propagator(sz[1:2]; Δz=sampling[3]/(λ/n), k_max=sampling[1:2]./(λ/n));

julia> prop3d = prop.^zz((1,1,sz[3])); # series of propagators for a stack
```

---

propagator(arr::AbstractArray; Δz=1.0, shift*by=(0,0), k*max=0.5, offset=CtrFt, scaling=ScaUnit)

This is a wrapper for  `propagator(eltype(arr), size(arr), Δz=Δz, shift_by=shift_by, k_max=k_max, scaling=scaling, offset=offset)`.
