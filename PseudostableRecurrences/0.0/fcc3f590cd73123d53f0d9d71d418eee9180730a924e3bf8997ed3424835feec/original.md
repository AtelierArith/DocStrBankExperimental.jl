```
BandedSylvesterRecurrence{T, TA<:AbstractMatrix{T}, TB<:AbstractMatrix{T}, TC<:AbstractMatrix{T}, TX<:AbstractMatrix{T}} <: AbstractLinearRecurrence{slicetype(TX)}
```

The recurrence generated from the infinite Sylvester equation $AX+XB+C=0$, assuming $X$ has infinite number of columns. The upper bandwidth of $A$ has to be finite, the lower bandwidth of $B$ has to be positive and finite and the lower bounding band of $B$ can't contain zero. The recurrence is basically a cross-shaped stencil recurrence, where the width of the stencil is determined by The total bandwidth of $B$ and the height by that of $A$. See also [`BandedSylvesterRecurrencePlan`](@ref).

!!! note
    The restriction to the bandwidths may not be optimal, but it's the boundary of our knowledge at the moment.


# Properties

  * `A::TA, B::TB, C::TC`: the matrices $A$, $B$ and $C$. It's recommended to use `BandedMatrices.jl` to boost performance. Their dimensions don't have to match. Just make sure that no `BoundsError` happens during the recurrence.
  * `buffer::TX`: the buffer that stores temp results.
  * `sliceind::Int`: the current column index.
  * `lastind::Int`: the last column index to be computed.
