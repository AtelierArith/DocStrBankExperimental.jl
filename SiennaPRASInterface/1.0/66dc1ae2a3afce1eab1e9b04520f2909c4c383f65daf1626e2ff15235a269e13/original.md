```
GeneratorStoragePRAS <: AbstractRAFormulation
```

Objects in Sienna that behave like generator and storage are mapped to generatorstorage in PRAS.

To add a generator storage formulation, you must also add a [`assign_to_gen_stor_matrices!`](@ref) function.

  * [`HybridSystemPRAS`](@ref)
  * [`HydroEnergyReservoirPRAS`](@ref)
