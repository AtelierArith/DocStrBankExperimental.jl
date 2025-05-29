`SelfCons{T<:Function, R<:Function, S<:Union{Number, Vector{<:Number}}}` is a data type representing a general function whose fixed point you want to calculate.

# Attributes

  * `F               ::  T`: The function for which the fixed point needs to be calulcated.
  * `F_args          ::  Tuple`: A tuple of arguments held fixed for the function `F`.
  * `F_kwargs        ::  Dict{Symbol, Any}`: a dictionary of keyword arguments helf fixed for the function `F`.
  * `Initial         ::  S` : the initial guess to start the fixed point iteration.
  * `VIns            ::  Vector{S}`: the history of all the inputs used throughout the fixed point iteration.
  * `VOuts           ::  Vector{S}`: the history of all the outputs used throughout the fixed point iteration.
  * `Update          ::  R`: the update method being used during the fixed point iteration. eg. [`SimpleMixing`](@ref).
  * `Update_kwargs   ::  Dict{Symbol, Any}`: some keyword arguments held fixed for the `Update` function.

Initialize this structure using 

```julia
SelfCons(F::T, Update::R, Initial::S ; F_args::Tuple = (), F_kwargs::Dict = Dict(), Update_kwargs::Dict = Dict()) where {T<:Function, R<:Function, S<:Union{Number, Vector{<:Number}}}
```
