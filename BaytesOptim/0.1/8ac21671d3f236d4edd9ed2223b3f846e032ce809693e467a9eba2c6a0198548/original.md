```julia
struct CustomAlgorithmDefault{I<:ModelWrappers.AbstractInitialization, U<:BaytesCore.UpdateBool}
```

Default arguments for Custom constructor.

# Fields

  * `init::ModelWrappers.AbstractInitialization`: Method to obtain initial Modelparameter, see 'AbstractInitialization'.
  * `generated::BaytesCore.UpdateBool`: Boolean if generate(_rng, objective) for corresponding model is stored in Algorithm Diagnostics.
