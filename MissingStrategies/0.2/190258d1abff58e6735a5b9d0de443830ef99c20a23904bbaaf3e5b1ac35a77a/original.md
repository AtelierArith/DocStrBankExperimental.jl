@handlemissings_typed(fun, ...)

Calling [`handlemissings`](@ref) with defaults tailored to an original method where the  eltype does not accepts missings:

  * Dispatching methods as with [`@handlemissings_stub`](@ref)
  * Argument type of the new function must be specified. May use `Any`. A default method (without `MissingStrategy` argument) is created that forwards to the  PassMissing method. Hence, Make sure that the argument type differs from the original method so that the original method its not overwritten.
  * PassMissing method calls the original method with an broadcast where each element has been converted to the corresponding nonmissing type ([`mgen.passmissing_convert`](@ref)).
  * SkipMissing method collects the skipmissing object before calling the original function ([`mgen.handlemissing_collect_skip`](@ref)).

Arguments: see [`handlemissings`](@ref)    

# Note on default MissingStrategy

Note, that defining a default Missingstrategy at an argument position before further  optional arguments behaves in a way that may not be intuitive.

```julia
f2(x::AbstractArray{<:Real},optarg=1:3) = x
@handlemissings_typed(f2(x::AbstractArray{<:Real},optarg=1:3)=0,1,2,Any)
# f2(x,ms::MissingStrategy=PassMissing(),optarg=1:3) # generated
# f2([1.0,missing], 2:4) # no method defined -> rethink argument ordering
```

In order to call the PassMissing variant in the above case, one would need to  call `@handle_missing_typed` separately for the method with a single and the method with two arguments  and place the default missing strategy behind the second argument in the second case.

```julia
f3(x::AbstractArray{<:Real},optarg=1:3) = x
@handlemissings_typed(f3(x::AbstractArray{<:Real})=0,1,2,Any)
@handlemissings_typed(f3(x::AbstractArray{<:Real}, optarg)=0,1,3,Any)
ismissing(f3([1.0,missing], 2:4))
```
