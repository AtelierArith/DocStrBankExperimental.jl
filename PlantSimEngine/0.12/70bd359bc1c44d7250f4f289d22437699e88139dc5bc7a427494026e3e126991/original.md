```
is_initialized(m::T) where T <: ModelList
is_initialized(m::T, models...) where T <: ModelList
```

Check if the variables that must be initialized are, and return `true` if so, and `false` and an information message if not.

# Note

There is no way to know before-hand which process will be simulated by the user, so if you have a component with a model for each process, the variables to initialize are always the smallest subset of all, meaning it is considered the user will simulate the variables needed for other models.

# Examples

```@example
using PlantSimEngine

# Load the dummy models given as example in the package:
using PlantSimEngine.Examples

models = ModelList(
    process1=Process1Model(1.0),
    process2=Process2Model(),
    process3=Process3Model()
)

is_initialized(models)
```
