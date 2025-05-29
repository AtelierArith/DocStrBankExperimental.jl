```
Legolas.SchemaVersion{name,version}
```

A type representing a particular version of Legolas schema. The relevant `name` (a `Symbol`) and `version` (an `Integer`) are surfaced as type parameters, allowing them to be utilized for dispatch.

For more details and examples, please see `Legolas.jl/examples/tour.jl` and the "Schema-Related Concepts/Conventions" section of the Legolas.jl documentation.

The constructor `SchemaVersion{name,version}()` will throw an `ArgumentError` if `version` is negative.

See also: [`Legolas.@schema`](@ref)
