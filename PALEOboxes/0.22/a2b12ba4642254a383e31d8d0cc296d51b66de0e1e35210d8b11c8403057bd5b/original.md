```
dispatch_methodlist(dl::ReactionMethodDispatchList, deltat::Float64=0.0)
dispatch_methodlist(dl::ReactionMethodDispatchList, pa::ParameterAggregator, deltat::Float64=0.0)
dispatch_methodlist(dl::ReactionMethodDispatchListNoGen, deltat::Float64=0.0)
dispatch_methodlist(dl::ReactionMethodDispatchListNoGen, pa::ParameterAggregator, deltat::Float64=0.0)
```

Call a list of ReactionMethods.

# Implementation

As an optimisation, with `dl::ReactionMethodDispatchList` uses @generated for Type stability and to avoid dynamic dispatch, instead of iterating over lists.

[`ReactionMethodDispatchList`](@ref) fields are Tuples hence are fully Typed, the @generated function emits unrolled code with a function call for each Tuple element. 
