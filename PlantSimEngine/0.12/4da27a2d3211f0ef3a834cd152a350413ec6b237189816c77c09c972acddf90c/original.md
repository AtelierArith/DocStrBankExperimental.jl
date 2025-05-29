```
outputs(model::AbstractModel)
outputs(...)
```

Get the outputs of one or several models.

Returns an empty tuple by default for `AbstractModel`s (no outputs) or `Missing` models.

# Examples

```jldoctest
using PlantSimEngine;

# Load the dummy models given as example in the package:
using PlantSimEngine.Examples;

outputs(Process1Model(1.0))

# output
(:var3,)
```
