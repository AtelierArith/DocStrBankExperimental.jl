```
struct Statement{T}
    node::T
    type::Any
end
```

A wrapper around `Core` nodes with an optional `type` field to allow for user-based local propagation and other forms of analysis. Usage of [`Builder`](@ref) or [`Canvas`](@ref) will automatically wrap or unwrap nodes when inserting or calling [`finish`](@ref) – so the user should never see `Statement` instances directly unless they are working on type propagation.

For more information on `Core` nodes, please see Julia's documentation on [lowered forms](https://docs.julialang.org/en/v1/devdocs/ast/#Lowered-form).
