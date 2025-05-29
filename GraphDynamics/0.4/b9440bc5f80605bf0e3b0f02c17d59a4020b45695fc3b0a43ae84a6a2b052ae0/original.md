computed_properties(::Subsystem{T}) :: NamedTuple{props, NTuple{N, funcs}}

Signal that a subsystem has properties which can be computed on-the-fly based on it's existing properties. In the termoinology used by ModelingToolkit.jl, these are "observed states".

This function takes in a `Subsystem` and returns a `NamedTuple` where each key is a property name that can be computed, and each value is a function that takes in the subsystem and returns a computed value.

By default, this function returns an empty NamedTuple.

Example:

```julia
struct Position end
function GraphDynamics.computed_properties(::Subsystem{Position})
    (;r = (;x, y) -> √(x^2 + y^2),
      θ = (;x, y) -> atan(y, x))
end

let sys = Subsystem{Position}(states=(x=1, y=2), params=(;))
    sys.r == √(sys.x^2 + sys.y^2)
end
```
