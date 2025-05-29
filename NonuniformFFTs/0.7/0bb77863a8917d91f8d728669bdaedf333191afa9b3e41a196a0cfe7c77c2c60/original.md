```
exec_type1!(ûs::AbstractArray{Z}, p::PlanNUFFT{T}, vp::AbstractVector{T})
exec_type1!(ûs::NTuple{N,AbstractArray{Z}}, p::PlanNUFFT{T}, vp::NTuple{N,AbstractVector{T}})
```

Perform type-1 NUFFT (from non-uniform points to uniform grid).

Here `vp` contains the input values at non-uniform points. The result of the transform is written into `ûs`.

One first needs to set the non-uniform points using [`set_points!`](@ref).

To perform multiple transforms at once, both `vp` and `ûs` should be a tuple of arrays (second variant above). Note that this requires a plan initialised with `ntransforms = Val(N)` (see [`PlanNUFFT`](@ref)).

The input types must satisfy `Z = complex(T)`. This means:

  * `Z = Complex{T}` for real-data transforms (where `T <: Real`);
  * `Z = T` for complex-data transforms (where `T <: Complex`).

See also [`exec_type2!`](@ref).
