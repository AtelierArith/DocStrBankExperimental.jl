```
exec_type2!(vp::AbstractVector{T}, p::PlanNUFFT{T}, ûs::AbstractArray{Z})
exec_type2!(vp::NTuple{N,AbstractVector{T}}, p::PlanNUFFT{T}, ûs::NTuple{N,AbstractArray{Z}})
```

Perform type-2 NUFFT (from uniform grid to non-uniform points).

Here `ûs` contains the input coefficients in the uniform grid. The result of the transform at non-uniform points is written into `vp`.

One first needs to set the non-uniform points using [`set_points!`](@ref).

To perform multiple transforms at once, both `vp` and `ûs` should be a tuple of arrays (second variant above). Note that this requires a plan initialised with `ntransforms = Val(N)` (see [`PlanNUFFT`](@ref)).

The input types must satisfy `Z = complex(T)`. This means:

  * `Z = Complex{T}` for real-data transforms (where `T <: Real`);
  * `Z = T` for complex-data transforms (where `T <: Complex`).

See also [`exec_type1!`](@ref).
