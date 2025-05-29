```
fmi2GetDirectionalDerivative(c::FMU2Component,
                                  vUnknown_ref::AbstractArray{fmi2ValueReference},
                                  vKnown_ref::AbstractArray{fmi2ValueReference},
                                  dvKnown::Union{AbstractArray{fmi2Real}, Nothing} = nothing)
```

Wrapper Function call to compute the partial derivative with respect to the variables `vKnown_ref`.

Computes the directional derivatives of an FMU. An FMU has different Modes and in every Mode an FMU might be described by different equations and different unknowns.The precise definitions are given in the mathematical descriptions of Model Exchange (section 3.1) and Co-Simulation (section 4.1). In every Mode, the general form of the FMU equations are: 𝐯*unknown = 𝐡(𝐯*known, 𝐯_rest)

  * `v_unknown`: vector of unknown Real variables computed in the actual Mode:

      * Initialization Mode: unkowns kisted under `<ModelStructure><InitialUnknowns>` that have type Real.
      * Continuous-Time Mode (ModelExchange): The continuous-time outputs and state derivatives. (= the variables listed under `<ModelStructure><Outputs>` with type Real and variability = `continuous` and the variables listed as state derivatives under `<ModelStructure><Derivatives>)`.
      * Event Mode (ModelExchange): The same variables as in the Continuous-Time Mode and additionally variables under `<ModelStructure><Outputs>` with type Real and variability = `discrete`.
      * Step Mode (CoSimulation):  The variables listed under `<ModelStructure><Outputs>` with type Real and variability = `continuous` or `discrete`. If `<ModelStructure><Derivatives>` is present, also the variables listed here as state derivatives.
  * `v_known`: Real input variables of function h that changes its value in the actual Mode.
  * `v_rest`:Set of input variables of function h that either changes its value in the actual Mode but are non-Real variables, or do not change their values in this Mode, but change their values in other Modes

Computes a linear combination of the partial derivatives of h with respect to the selected input variables 𝐯_known:

```
Δv_unknown = (δh / δv_known) Δv_known
```

# Arguments

  * `c::FMU2Component`: Mutable struct represents an instantiated instance of an FMU in the FMI 2.0.2 Standard.
  * `vUnknown_ref::AbstractArray{fmi2ValueReference}`: Argument `vUnknown_ref` contains values of type`fmi2ValueReference` which are identifiers of a variable value of the model. `vUnknown_ref` can be equated with `v_unknown`(variable described above).
  * `vKnown_ref::AbstractArray{fmi2ValueReference}`: Argument `vKnown_ref` contains values of type `fmi2ValueReference` which are identifiers of a variable value of the model.`vKnown_ref` can be equated with `v_known`(variable described above).
  * `dvKnown::Union{AbstractArray{fmi2Real}, Nothing} = nothing`: If no seed vector is passed the value `nothing` is used. The vector values Compute the partial derivative with respect to the given entries in vector `vKnown_ref` with the matching evaluate of `dvKnown`.  # gehört das zu den v_rest values

# Returns

  * `dvUnknown::Array{fmi2Real}`: Return `dvUnknown` contains the directional derivative vector values.

# Source

  * FMISpec2.0.2 Link: [https://fmi-standard.org/](https://fmi-standard.org/)
  * FMISpec2.0.2[p.16]: 2.1.2 Platform Dependent Definitions (fmi2TypesPlatform.h)
  * FMISpec2.0.2[p.16]: 2.1.3 Status Returned by Functions
  * FMISpec2.0.2[p.25]: 2.1.9 Getting Partial Derivatives

See also [`fmi2GetDirectionalDerivative!`](@ref).
