```julia
mutable struct JumpProblem{iip, P, A, C, J<:Union{Nothing, DiffEqJump.AbstractJumpAggregator}, J2, J3, J4, R} <: SciMLBase.AbstractJumpProblem{P, J<:Union{Nothing, DiffEqJump.AbstractJumpAggregator}}
```

Defines a collection of jump processes to associate with another problem type.

  * [Documentation Page](https://jump.sciml.ai/stable/jump_types/)
  * [Tutorial Page](https://jump.sciml.ai/stable/tutorials/discrete_stochastic_example/)
  * [FAQ Page](https://jump.sciml.ai/stable/tutorials/discrete_stochastic_example/#FAQ)

### Constructors

`JumpProblem`s can be constructed by first building another problem type to which the jumps will be associated. For example, to  simulate a collection of jump processes for which the transition rates are constant *between* jumps (called [`ConstantRateJump`](@ref)s or [`MassActionJump`](@ref)s), we must first construct a [`DiscreteProblem`](https://docs.sciml.ai/dev/modules/DiffEqDocs/types/discrete_types/)

```julia
prob = DiscreteProblem(u0, p, tspan)
```

where `u0` is the initial condition, `p` the parameters and `tspan` the time span. If we wanted to have the jumps coupled with a system of ODEs, or have transition rates with explicit time dependence, we would use an `ODEProblem` instead that defines the ODE portion of the dynamics.

Given `prob` we define the jumps via

  * `JumpProblem(prob, aggregator::AbstractAggregatorAlgorithm, jumps::JumpSet ; kwargs...)`
  * `JumpProblem(prob, aggregator::AbstractAggregatorAlgorithm, jumps...; kwargs...)`

Here `aggregator` specifies the underlying algorithm for calculating next jump times and types, for example [`Direct`](@ref). The collection of different `AbstractJump` types can then be passed within a single [`JumpSet`](@ref) or as subsequent sequential arguments.

### Fields

  * `prob`: The type of problem to couple the jumps to. For a pure jump process use `DiscreteProblem`, to couple to ODEs, `ODEProblem`, etc.
  * `aggregator`: The aggregator algorithm that determines the next jump times and types for `ConstantRateJump`s and `MassActionJump`s. Examples include `Direct`.
  * `discrete_jump_aggregation`: The underlying state data associated with the chosen aggregator.
  * `jump_callback`: `CallBackSet` with the underlying `ConstantRate` and `VariableRate` jumps.
  * `variable_jumps`: The `VariableRateJump`s.
  * `regular_jump`: The `RegularJump`s.
  * `massaction_jump`: The `MassActionJump`s.
  * `rng`: The random number generator to use.

## Keyword Arguments

  * `rng`, the random number generator to use. On 1.7 and up defaults to Julia's builtin generator, below 1.7 uses RandomNumbers.jl's `Xorshifts.Xoroshiro128Star(rand(UInt64))`.
  * `save_positions=(true,true)`, specifies whether to save the system's state (before,after) the jump occurs.
  * `spatial_system`, for spatial problems the underlying spatial structure.
  * `hopping_constants`, for spatial problems the spatial transition rate coefficients.

Please see the [tutorial page](https://jump.sciml.ai/stable/tutorials/discrete_stochastic_example/) in the DifferentialEquations.jl [docs](https://jump.sciml.ai/stable/) for usage examples and commonly asked questions.
