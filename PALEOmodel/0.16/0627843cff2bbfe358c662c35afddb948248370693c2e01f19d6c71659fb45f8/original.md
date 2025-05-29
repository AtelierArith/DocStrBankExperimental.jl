```
initialize!(model::PB.Model; kwargs...) -> (initial_state::Vector, modeldata::PB.ModelData)
```

Initialize `model` and return:

  * an `initial_state` Vector
  * a `modeldata` struct containing the model arrays.

# Initialising the state vector

With default arguments, the `model` state variables are initialised to the values defined in the `.yaml` configuration file used to create the `model`.

The optional `pickup_output` argument can be used to provide an `OutputWriter` instance with pickup data to initialise from, using [`set_statevar_from_output!`](@ref). This is applied afer the default initialisation, hence can be used to (re)initialise a subset of model state variables.

# `DataType`s for model arrays

With default arguments, the `model` arrays use `Float64` as the element type. The `eltype` keyword argument can be used to specify a different Julia `DataType`, eg for use with automatic differentiation.  Per-Variable `DataType` can be specified by using the `:datatype` Variable attribute to specify `String`-valued tags, in combination with the `eltypemap` keyword argument to  provide a `Dict` of tag names => `DataType`s. 

# Thread safety

A thread-safe model can be created by setting the `threadsafe=true` global parameter in the YAML config file before calling `PB.create_model_from_config`  (used by Reactions that require eg special handling of global accumulator variables to maintain thread safety), and supplying `method_barrier` (a thread barrier to add to `ReactionMethod` dispatch lists between dependency-free groups):

```
method_barrier = PB.reaction_method_thread_barrier(
    PALEOmodel.ThreadBarriers.ThreadBarrierAtomic("the barrier"),
    PALEOmodel.ThreadBarriers.wait_barrier
)
```

# Keyword summary

  * `pickup_output=nothing`: OutputWriter with pickup data to initialise from
  * `check_units_opt=:no`: check linked Variable units are consistent (:no to disable check, :warn to warn and continue, :error to error and stop)
  * `eltype::Type=Float64`: default data type to use for model arrays
  * `eltypemap=Dict{String, DataType}()`: Dict of data types to look up Variable :datatype attribute
  * `method_barrier=nothing`: thread barrier to add to dispatch lists to create a thread-safe model
  * `expect_hostdep_varnames=["global.tforce"]`: non-state-Variable host-dependent Variable names expected
  * `SolverView_all=true`: `true` to create `modeldata.solver_view_all`
  * `create_dispatchlists_all=true`: `true` to create `modeldata.dispatchlists_all`
  * `generated_dispatch=true`: `true` to autogenerate code for `modeldata.dispatchlists_all` (fast dispatch, slow compile)
