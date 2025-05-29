```
variables(model)
variables(model, models...)
```

Returns a tuple with the name of the variables needed by a model, or a union of those variables for several models.

# Note

Each model can (and should) have a method for this function.

```jldoctest

using PlantSimEngine;

# Load the dummy models given as example in the package:
using PlantSimEngine.Examples;

variables(Process1Model(1.0))

variables(Process1Model(1.0), Process2Model())

# output

(var1 = -Inf, var2 = -Inf, var3 = -Inf, var4 = -Inf, var5 = -Inf)
```

# See also

[`inputs`](@ref), [`outputs`](@ref) and [`variables_typed`](@ref)
