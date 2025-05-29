```
init_status!(object::Dict{String,ModelList};vars...)
init_status!(component::ModelList;vars...)
```

Initialise model variables for components with user input.

# Examples

```@example
using PlantSimEngine

# Load the dummy models given as example in the package:
using PlantSimEngine.Examples

models = Dict(
    "Leaf" => ModelList(
        process1=Process1Model(1.0),
        process2=Process2Model(),
        process3=Process3Model()
    ),
    "InterNode" => ModelList(
        process1=Process1Model(1.0),
    )
)

init_status!(models, var1=1.0 , var2=2.0)
status(models["Leaf"])
```
