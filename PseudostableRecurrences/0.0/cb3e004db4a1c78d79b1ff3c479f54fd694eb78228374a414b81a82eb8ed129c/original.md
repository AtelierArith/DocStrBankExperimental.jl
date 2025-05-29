```
BandedSylvesterRecurrencePlan{FA<:Function, FB<:Function, FC<:Function, INIT<:Function} <: AbstractLinearRecurrencePlan
```

See also [`BandedSylvesterRecurrence`](@ref).

# Properties

  * `fA::FA, fB::FB, fC::FC`: the functions that generate `A`, `B` and `C` for the `BandedSylvesterRecurrence`. The functions should have the form `f(eltype, size...)`.
  * `init::INIT`: the function that generates the first few columns of $X$ in order to start the recurrence. It should have the form `f(eltype, size...)`.
  * `size::Dims{2}`: the size of $X$.
  * `bandB::NTuple{2,Int}`: the bandwidths of `B`. Although `B` can have infinite upper bandwidth, that will cause the stencil to have infinite width and hence in practice, the upper bandwidth of `B` is always limited by the finite width of $X$.
  * `firstind::Int`: the first column to be computed. The default value is `bandB[2]+1`.
