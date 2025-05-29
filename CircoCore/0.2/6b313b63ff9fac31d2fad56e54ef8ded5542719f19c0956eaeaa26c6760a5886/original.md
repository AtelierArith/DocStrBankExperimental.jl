```
abstract type Actor{TCoreState}
```

Supertype of all actors.

Subtypes must be mutable and must provide a field `core::TCoreState` that can remain undefined after creation.

# Examples

```julia
mutable struct DataHolder{TValue, TCore} <: Actor{TCore}
    value::TValue
    core::TCore
end
```
