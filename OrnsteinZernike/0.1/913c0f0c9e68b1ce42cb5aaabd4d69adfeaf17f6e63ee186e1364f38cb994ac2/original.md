```
CustomPotential
```

Implements a potential that evaluates a user defined function.

Expects values `f`, and `p`, which respecively are a callable and a list of parameters. The function should be called `f(r::Number, p)` and it should produce either a `Number`, in the case of a single-component system, or an `SMatrix`, in the case of a multicomponent system. 

Example:

```julia
f = (r, p) -> 4*p[1]*((p[2]/r)^12 -  (p[2]/r)^6)
potential = CustomPotential(f, (1.0, 1.0))
```
