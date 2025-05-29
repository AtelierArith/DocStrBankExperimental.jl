```
macro DDSmodel
```

Macro for creating a DDS (discrete dynamical system)  from a list of equations. It also injects all variables into the global scope.

## Example

Creating a simple `DDS`:

```jldoctest
using StructuralIdentifiability

dds = @DDSmodel(
    x1(t + 1) = a * x1(t) + u(t),
    x2(t + 1) = b * x2(t) + c*x1(t)*x2(t),
    y(t) = x1(t)
)
```

Here,

  * `x1`, `x2` are state variables
  * `y` is an output variable
  * `u` is an input variable
  * `a`, `b`, `c` are time-independent parameters
