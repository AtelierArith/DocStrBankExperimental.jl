```
struct Equation <: AbstractEquation ⋯ end
```

Data type representing a single equation in a model.

Equations are defined in [`@equations`](@ref) blocks. The actual equation instances are later created with [`@initialize`](@ref) and stored within the model object.

Equation flags can be specified by annotating the equation definition with one or more `@<flag>`. See [`EqnFlags`](@ref) for details.

Each equation has two functions associated with it, one which computes the residual and the other computes both the residual and the gradient . Usually there's no need to users to call these functions directly. They are used internally by the solvers.
