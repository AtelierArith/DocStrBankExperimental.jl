```
inputs(model::AbstractModel)
inputs(...)
```

Get the inputs of one or several models.

Returns an empty tuple by default for `AbstractModel`s (no inputs) or `Missing` models.

# Examples

```jldoctest
using PlantSimEngine;

# Load the dummy models given as example in the package:
using PlantSimEngine.Examples;

inputs(Process1Model(1.0))

# output
(:var1, :var2)
```
