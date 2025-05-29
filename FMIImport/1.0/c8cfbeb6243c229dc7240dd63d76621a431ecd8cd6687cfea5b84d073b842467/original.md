```
fmi2GetDirectionalDerivative!(c::FMU2Component,
                                   vUnknown_ref::AbstractArray{fmi2ValueReference},
                                   nUnknown::Csize_t,
                                   vKnown_ref::AbstractArray{fmi2ValueReference},
                                   nKnown::Csize_t,
                                   dvKnown::AbstractArray{fmi2Real},
                                   dvUnknown::AbstractArray{fmi2Real})
```

Wrapper Function call to compute the partial derivative with respect to the variables `vKnown_ref`.

Computes the directional derivatives of an FMU. An FMU has different Modes and in every Mode an FMU might be described by different equations and different unknowns. The precise definitions are given in the mathematical descriptions of Model Exchange (section 3.1) and Co-Simulation (section 4.1). In every Mode, the general form of the FMU equations are: 𝐯*unknown = 𝐡(𝐯*known, 𝐯_rest)

  * `v_unknown`: vector of unknown Real variables computed in the actual Mode:

      * Initialization Mode: unkowns kisted under `<ModelStructure><InitialUnknowns>` that have type Real.
      * Continuous-Time Mode (ModelExchange): The continuous-time outputs and state derivatives. (= the variables listed under `<ModelStructure><Outputs>` with type Real and variability = `continuous` and the variables listed as state derivatives under `<ModelStructure><Derivatives>)`.
      * Event Mode (ModelExchange): The same variables as in the Continuous-Time Mode and additionally variables under `<ModelStructure><Outputs>` with type Real and variability = `discrete`.
      * Step Mode (CoSimulation):  The variables listed under `<ModelStructure><Outputs>` with type Real and variability = `continuous` or `discrete`. If `<ModelStructure><Derivatives>` is present, also the variables listed here as state derivatives.
  * `v_known`: Real input variables of function h that changes its value in the actual Mode.
  * `v_rest`:Set of input variables of function h that either changes its value in the actual Mode but are non-Real variables, or do not change their values in this Mode, but change their values in other Modes

Computes a linear combination of the partial derivatives of h with respect to the selected input variables 𝐯_known:

Δv*unknown = (δh / δv*known) Δv_known

# Arguments

  * `c::FMU2Component`: Mutable struct represents an instantiated instance of an FMU in the FMI 2.0.2 Standard.
  * `vUnknown_ref::AbstracArray{fmi2ValueReference}`: Argument `vUnknown_ref` contains values of type`fmi2ValueReference` which are identifiers of a variable value of the model. `vUnknown_ref` can be equated with `v_unknown`(variable described above).
  * `nUnknown::Csize_t`: Length of the `Unknown` Array.
  * `vKnown_ref::AbstractArray{fmi2ValueReference}`: Argument `vKnown_ref` contains values of type `fmi2ValueReference` which are identifiers of a variable value of the model.`vKnown_ref` can be equated with `v_known`(variable described above).
  * `nKnown::Csize_t`: Length of the `Known` Array.
  * `dvKnown::AbstractArray{fmi2Real}`:The vector values Compute the partial derivative with respect to the given entries in vector `vKnown_ref` with the matching evaluate of `dvKnown`.
  * `dvUnknown::AbstractArray{fmi2Real}`: Stores the directional derivative vector values.

# Returns

  * `status::fmi2Status`: Return `status` is an enumeration of type `fmi2Status` and indicates the success of the function call.

More detailed:

  * `fmi2OK`: all well
  * `fmi2Warning`: things are not quite right, but the computation can continue
  * `fmi2Discard`: if the slave computed successfully only a subinterval of the communication step
  * `fmi2Error`: the communication step could not be carried out at all
  * `fmi2Fatal`: if an error occurred which corrupted the FMU irreparably
  * `fmi2Pending`: this status is returned if the slave executes the function asynchronously

# Source

  * FMISpec2.0.2 Link: [https://fmi-standard.org/](https://fmi-standard.org/)
  * FMISpec2.0.2[p.16]: 2.1.2 Platform Dependent Definitions (fmi2TypesPlatform.h)
  * FMISpec2.0.2[p.16]: 2.1.3 Status Returned by Functions
  * FMISpec2.0.2[p.25]: 2.1.9 Getting Partial Derivatives

See also [`fmi2GetDirectionalDerivative!`](@ref).
