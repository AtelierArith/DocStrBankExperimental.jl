```
ModelList(models::M, status::S)
ModelList(;
    status=nothing,
    type_promotion=nothing,
    variables_check=true,
    kwargs...
)
```

List the models for a simulation (`models`), and does all boilerplate for variable initialization,  type promotion, time steps handling.

!!! note
    The status field depends on the input models. You can get the variables needed by a model using [`variables`](@ref) on the instantiation of a model. You can also use [`inputs`](@ref) and [`outputs`](@ref) instead.


# Arguments

  * `models`: a list of models. Usually given as a `NamedTuple`, but can be any other structure that

implements `getproperty`.

  * `status`: a structure containing the initializations for the variables of the models. Usually a NamedTuple

when given as a kwarg, or any structure that implements the Tables interface from `Tables.jl` (*e.g.* DataFrame, see details).

  * `type_promotion`: optional type conversion for the variables with default values.

`nothing` by default, *i.e.* no conversion. Note that conversion is not applied to the variables input by the user as `kwargs` (need to do it manually). Should be provided as a Dict with current type as keys and new type as values.

  * `variables_check=true`: check that all needed variables are initialized by the user.
  * `kwargs`: the models, named after the process they simulate.

# Details

If you need to input a custom Type for the status and make your users able to only partially initialize  the `status` field in the input, you'll have to implement a method for `add_model_vars!`, a function that  adds the models variables to the type in case it is not fully initialized. The default method is compatible  with any type that implements the `Tables.jl` interface (*e.g.* DataFrame), and `NamedTuples`.

Note that `ModelList`makes a copy of the input `status` if it does not list all needed variables.

## Examples

We'll use the dummy models from the `dummy.jl` in the examples folder of the package. It  implements three dummy processes: `Process1Model`, `Process2Model` and `Process3Model`, with one model implementation each: `Process1Model`, `Process2Model` and `Process3Model`.

```jldoctest 1
julia> using PlantSimEngine;
```

Including example processes and models:

```jldoctest 1
julia> using PlantSimEngine.Examples;
```

```jldoctest 1
julia> models = ModelList(process1=Process1Model(1.0), process2=Process2Model(), process3=Process3Model());
[ Info: Some variables must be initialized before simulation: (process1 = (:var1, :var2), process2 = (:var1,)) (see `to_initialize()`)
```

```jldoctest 1
julia> typeof(models)
ModelList{@NamedTuple{process1::Process1Model, process2::Process2Model, process3::Process3Model}, Status{(:var5, :var4, :var6, :var1, :var3, :var2), NTuple{6, Base.RefValue{Float64}}}}
```

No variables were given as keyword arguments, that means that the status of the ModelList is not set yet, and all variables are initialized to their default values given in the inputs and outputs (usually `typemin(Type)`, *i.e.* `-Inf` for floating point numbers). This component cannot be simulated yet.

To know which variables we need to initialize for a simulation, we use [`to_initialize`](@ref):

```jldoctest 1
julia> to_initialize(models)
(process1 = (:var1, :var2), process2 = (:var1,))
```

We can now provide values for these variables in the `status` field, and simulate the `ModelList`,  *e.g.* for `process3` (coupled with `process1` and `process2`):

```jldoctest 1
julia> models = ModelList(process1=Process1Model(1.0), process2=Process2Model(), process3=Process3Model(), status=(var1=15.0, var2=0.3));
```

```jldoctest 1
julia> meteo = Atmosphere(T = 22.0, Wind = 0.8333, P = 101.325, Rh = 0.4490995);
```

```jldoctest 1
julia> outputs_sim = run!(models,meteo)
TimeStepTable{Status{(:var5, :var4, :var6, ...}(1 x 6):
╭─────┬─────────┬─────────┬─────────┬─────────┬─────────┬─────────╮
│ Row │    var5 │    var4 │    var6 │    var1 │    var3 │    var2 │
│     │ Float64 │ Float64 │ Float64 │ Float64 │ Float64 │ Float64 │
├─────┼─────────┼─────────┼─────────┼─────────┼─────────┼─────────┤
│   1 │ 36.0139 │    22.0 │ 58.0139 │    15.0 │     5.5 │     0.3 │
╰─────┴─────────┴─────────┴─────────┴─────────┴─────────┴─────────╯
```

```jldoctest 1
julia> outputs_sim[:var6]
1-element Vector{Float64}:
 58.0138985
```

If we want to use special types for the variables, we can use the `type_promotion` argument:

```jldoctest 1
julia> models = ModelList(process1=Process1Model(1.0), process2=Process2Model(), process3=Process3Model(), status=(var1=15.0, var2=0.3), type_promotion = Dict(Float64 => Float32));
```

We used `type_promotion` to force the status into Float32:

```jldoctest 1
julia> [typeof(models[i][1]) for i in keys(status(models))]
6-element Vector{DataType}:
 Float32
 Float32
 Float32
 Float64
 Float64
 Float32
```

But we see that only the default variables (the ones that are not given in the status arguments) were converted to Float32, the two other variables that we gave were not converted. This is because we want to give the ability to users to give any type for the variables they provide  in the status. If we want all variables to be converted to Float32, we can pass them as Float32:

```jldoctest 1
julia> models = ModelList(process1=Process1Model(1.0), process2=Process2Model(), process3=Process3Model(), status=(var1=15.0f0, var2=0.3f0), type_promotion = Dict(Float64 => Float32));
```

We used `type_promotion` to force the status into Float32:

```jldoctest 1
julia> [typeof(models[i][1]) for i in keys(status(models))]
6-element Vector{DataType}:
 Float32
 Float32
 Float32
 Float32
 Float32
 Float32
```
