```
macro ODEmodel
```

Macro for creating an ODE from a list of equations. It also injects all variables into the global scope.

## Example

Creating a simple `ODE`:

```jldoctest
using StructuralIdentifiability

ode = @ODEmodel(
    x1'(t) = a * x1(t) + u(t),
    x2'(t) = b * x2(t) + c*x1(t)*x2(t),
    y(t) = x1(t)
)
```

Here,

  * `x1`, `x2` are state variables
  * `y` is an output variable
  * `u` is an input variable
  * `a`, `b`, `c` are time-independent parameters
