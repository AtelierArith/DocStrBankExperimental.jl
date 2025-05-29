```
InitiatorRule{V}
```

Abstract type for defining initiator rules for [`InitiatorDVec`](@ref). Concrete implementations:

  * [`Initiator`](@ref)
  * [`SimpleInitiator`](@ref)
  * [`CoherentInitiator`](@ref)
  * [`NonInitiator`](@ref)

# Extended Help

`InitiatorRule`s define how to store and retrieve data from associated [`AbstractInitiatorValue`](@ref)s. When defining a new `InitiatorRule`, also define the following:

  * [`initiator_valtype`](@ref)
  * [`from_initiator_value`](@ref)
  * [`to_initiator_value`](@ref)
