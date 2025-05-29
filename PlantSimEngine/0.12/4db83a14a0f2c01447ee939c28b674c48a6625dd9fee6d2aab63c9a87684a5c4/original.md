```
to_initialize(; verbose=true, vars...)
to_initialize(m::T)  where T <: ModelList
to_initialize(m::DependencyGraph)
to_initialize(mapping::Dict{String,T}, graph=nothing)
```

Return the variables that must be initialized providing a set of models and processes. The function takes into account model coupling and only returns the variables that are needed considering that some variables that are outputs of some models are used as inputs of others.

# Arguments

  * `verbose`: if `true`, print information messages.
  * `vars...`: the models and processes to consider.
  * `m::T`: a [`ModelList`](@ref).
  * `m::DependencyGraph`: a [`DependencyGraph`](@ref).
  * `mapping::Dict{String,T}`: a mapping that associates models to organs.
  * `graph`: a graph representing a plant or a scene, *e.g.* a multiscale tree graph. The graph is used to check if variables that are not initialized can be found in the graph nodes attributes.

# Examples

```@example
using PlantSimEngine

# Load the dummy models given as example in the package:
using PlantSimEngine.Examples

to_initialize(process1=Process1Model(1.0), process2=Process2Model())

# Or using a component directly:
models = ModelList(process1=Process1Model(1.0), process2=Process2Model())
to_initialize(models)

m = ModelList(
    (
        process1=Process1Model(1.0),
        process2=Process2Model()
    ),
    Status(var1 = 5.0, var2 = -Inf, var3 = -Inf, var4 = -Inf, var5 = -Inf)
)

to_initialize(m)
```

Or with a mapping:

```@example
using PlantSimEngine

# Load the dummy models given as example in the package:
using PlantSimEngine.Examples

mapping = Dict(
    "Leaf" => ModelList(
        process1=Process1Model(1.0),
        process2=Process2Model(),
        process3=Process3Model()
    ),
    "Internode" => ModelList(
        process1=Process1Model(1.0),
    )
)

to_initialize(mapping)
```
