```
fmi3GetAdjointDerivative!(c::FMU3Instance,
            unknowns::AbstractArray{fmi3ValueReference},
            nUnknowns::Csize_t,
            knowns::AbstractArray{fmi3ValueReference},
            nKnowns::Csize_t,
            seed::AbstractArray{fmi3Float64},
            nSeed::Csize_t,
            sensitivity::AbstractArray{fmi3Float64},
            nSensitivity::Csize_t)
```

Wrapper Function call to compute the partial derivative with respect to the variables `unknowns`.

Computes the adjoint derivatives of an FMU. An FMU has different Modes and in every Mode an FMU might be described by different equations and different unknowns. The precise definitions are given in the mathematical descriptions of Model Exchange (section 3) and Co-Simulation (section 4). In every Mode, the general form of the FMU equations are: unknowns = 𝐡(knowns, rest)

  * `unknowns`: vector of unknown Real variables computed in the actual Mode:
  * Initialization Mode: unkowns kisted under `<ModelStructure><InitialUnknown>` that have type Real.
  * Continuous-Time Mode (ModelExchange): The continuous-time outputs and state derivatives. (= the variables listed under `<ModelStructure><Output>` with type Real and variability = `continuous` and the variables listed as state derivatives under `<ModelStructure><ContinuousStateDerivative>)`.
  * Event Mode (ModelExchange/CoSimulation): The same variables as in the Continuous-Time Mode and additionally variables under `<ModelStructure><Output>` with type Real and variability = `discrete`.
  * Step Mode (CoSimulation):  The variables listed under `<ModelStructure><Output>` with type Real and variability = `continuous` or `discrete`. If `<ModelStructure><ContinuousStateDerivative>` is present, also the variables listed here as state derivatives.
  * `knowns`: Real input variables of function h that changes its value in the actual Mode.
  * `rest`: Set of input variables of function h that either changes its value in the actual Mode but are non-Real variables, or do not change their values in this Mode, but change their values in other Modes

Computes a linear combination of the partial derivatives of h with respect to the selected input variables 𝐯_known:

Δunknowns = (δh / δknowns) Δknowns

# Arguments

  * `c::FMU3Instance`: Mutable struct represents an instantiated instance of an FMU in the FMI 3.0 Standard.
  * `unknowns::AbstracArray{fmi3ValueReference}`: Argument `unknowns` contains values of type`fmi3ValueReference` which are identifiers of a variable value of the model. `unknowns` can be equated with `unknowns`(variable described above).
  * `nUnknowns::Csize_t`:
  * `knowns::AbstractArray{fmi3ValueReference}`: Argument `knowns` contains values of type `fmi3ValueReference` which are identifiers of a variable value of the model.`knowns` can be equated with `knowns`(variable described above).
  * `nKnowns::Csize_t`:
  * `seed::AbstractArray{fmi3Float64}`:The vector values Compute the partial derivative with respect to the given entries in vector `knowns` with the matching evaluate of `sensitivity`.
  * `nKnowns::Csize_t`:
  * `sensitivity::AbstractArray{fmi3Float64}`: Stores the adjoint derivative vector values.
  * `nKnowns::Csize_t`:

# Returns

  * `status::fmi3Status`: Return `status` is an enumeration of type `fmi3Status` and indicates the success of the function call.

More detailed:

  * `fmi3OK`: all well
  * `fmi3Warning`: things are not quite right, but the computation can continue
  * `fmi3Discard`: if the slave computed successfully only a subinterval of the communication step
  * `fmi3Error`: the communication step could not be carried out at all
  * `fmi3Fatal`: if an error occurred which corrupted the FMU irreparably

# Source

  * FMISpec3.0 Link: [https://fmi-standard.org/](https://fmi-standard.org/)
  * FMISpec3.0: 2.2.3 Platform Dependent Definitions
  * FMISpec3.0: 2.2.4 Status Returned by Functions
  * FMISpec3.0: 2.2.11. Getting Partial Derivatives

See also [`fmi3GetAdjointDerivative!`](@ref).
