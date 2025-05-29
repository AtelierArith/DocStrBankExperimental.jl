```
@fix_show constructor::T
```

Overload `Base.show` to get a human readable display of all objects of the form `constructor(args...; kwargs...)`, given an upper bound `T` for the type of such objects, that does not supertype any other objects.

# Example

Consider this definition of a constructor `LP`:

```julia
import StatisticalMeasuresBase as API
using StatisticalMeasuresBase

struct LPOnScalars{T}
    p::T
end
measure(yhat, y) = abs(yhat - y)^measure.p

LP(; p=2) = multimeasure(LPOnScalars(p))

julia> LP()
multimeasure(LPOnScalars{Int64}(2))
```

We fix this as follows:

```julia
LPType = API.Multimeasure{<:LPOnScalars}
@fix_show LP::LPType

julia> LP()
LP(
  p = 2)
```
