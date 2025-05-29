```
InjectorControl(target, mix, density = 1.0, phases = ((1, 1.0)), temperature = 293.15)
```

Well control that specifies injection into the reservoir. `target` specifies the type of target and `mix` defines the injection mass fractions for all species in the model during injection. 

For example, for a three-component system made up of CO2, H2O and H2, setting [0.1, 0.6, 0.3] would mean that the injection stream would contain 1 part CO2, 6 parts H2O and 3 parts H2 by mass. For an immiscible system (e.g. `LiquidPhase(), VaporPhase()`) the species corresponds to phases and [0.3, 0.7] would mean a 3 to 7 mixture of liquid and vapor by mass.

The density of the injected fluid at surface conditions is given by `density` which is defaulted to 1.0 if not given.

See also [`ProducerControl`](@ref), [`DisabledControl`](@ref).
