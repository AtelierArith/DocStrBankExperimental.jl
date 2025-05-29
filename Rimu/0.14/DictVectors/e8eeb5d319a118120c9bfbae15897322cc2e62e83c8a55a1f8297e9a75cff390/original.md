```
InitiatorDVec{K,V} <: AbstractDVec{K,V}
```

Dictionary-based vector-like data structure for use with [`ProjectorMonteCarloProblem`](@ref Main.ProjectorMonteCarloProblem) and [`KrylovKit.jl`](https://github.com/Jutho/KrylovKit.jl). See [`AbstractDVec`](@ref). Functionally identical to [`DVec`](@ref), but contains [`InitiatorValue`](@ref)s internally in order to facilitate initiator methods. Initiator methods for controlling the Monte Carlo sign problem were first introduced in [J. Chem. Phys. 132, 041103 (2010)](https://doi.org/10.1063/1.3302277). How the initiators are handled is controlled by specifying an [`InitiatorRule`](@ref) with the `initiator` keyword argument (see below).

See also: [`AbstractDVec`](@ref), [`DVec`](@ref), [`PDVec`](@ref).

## Constructors

  * `InitiatorDVec(dict::AbstractDict[; style, initiator, capacity])`: create an `InitiatorDVec` with `dict` for storage.  Note that the data may or may not be copied.
  * `InitiatorDVec(args...[; style, initiator, capacity])`: `args...` are passed to the `Dict` constructor. The `Dict` is used for storage.
  * `InitiatorDVec{K,V}([; style, initiator, capacity])`: create an empty `InitiatorDVec{K,V}`.
  * `InitiatorDVec(dv::AbstractDVec[; style, initiator, capacity])`: create an `InitiatorDVec`  with the same contents as `dv`. The `style` is inherited from `dv` by default.

## Keyword  arguments

  * `style`: A valid [`StochasticStyle`](@ref).  The default is selected based on the `InitiatorDVec`'s `valtype` (see [`default_style`](@ref)). If a style is given and the `valtype` does not match the `style`'s `eltype`, the values are converted to an appropriate type.
  * `initiator = Initiator(1)`: A valid [`InitiatorRule`](@ref). See [`Initiator`](@ref).
  * `capacity`: Indicative size as `Int`. Optional. Sets the initial size of the `InitiatorDVec` via `Base.sizehint!`.
