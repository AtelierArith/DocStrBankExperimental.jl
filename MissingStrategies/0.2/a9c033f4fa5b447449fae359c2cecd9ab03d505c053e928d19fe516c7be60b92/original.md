@handlemissings_stub(fun, ...)

Calling [`handlemissings`](@ref) with just creating the disaptching matches but no implementations yet that handling missings.

  * Default to using argument type Any and providing no default strategy  (use arguments to change this.)
  * Method with inserted MissingStrategy argument that forwards to the dispatching function
  * A dispaching method for eltypes not allowing for missings for any MissingStrategy that calls the original function without the MissingStrategy.

Arguments: see [`handlemissings`](@ref)    

One then can define the other methods yourself using Simpletraits `@traitfn`.

```jldoctest; output=false
using SimpleTraits
f1(x::AbstractArray{<:Real}) = "method that is not accepting missings in eltype"
@handlemissings_stub(
  # signature matching that of the original function to be called
  f1(x::AbstractArray{<:Real}) = 0,
  # pos_missing, pos_strategy, type_missing, defaultstrategy
  1,2,AbstractArray{<:Union{Missing,Real}}, PassMissing()
) 
methods(f1) # just to see that new methods have been defined
# the new methods forward to new function f1_hm that can be extended for special cases
# note the argument order: missing strategy comes first in the dispatching function
@traitfn function f1_hm(ms::PassMissing, x::::IsEltypeSuperOfMissing) 
  "method handling missings in eltype"
end
f1([1.0,2.0]) == "method that is not accepting missings in eltype"
f1([1.0,2.0], PassMissing()) == "method that is not accepting missings in eltype"
f1([1.0,2.0,missing]) == "method handling missings in eltype"
# output
true
```
