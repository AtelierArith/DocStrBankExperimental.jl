```
init_variables(models...)
```

Initialized model variables with their default values. The variables are taken from the inputs and outputs of the models.

# Examples

```@example
using PlantSimEngine

# Load the dummy models given as example in the package:
using PlantSimEngine.Examples

init_variables(Process1Model(2.0))
init_variables(process1=Process1Model(2.0), process2=Process2Model())
```
