```
detect_stateless(detect::Bool = true)
```

Per default, Vahana expects that the :Stateless hint is set manually.

This design decision was made so as not to confuse users, since then, for example, the [`edges`](@ref) is not available.

This behaviour can be customized by calling `detect_stateless` before calling [`register_edgetype!`](@ref).
