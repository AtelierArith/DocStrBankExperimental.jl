```
add_equation!(model::Model, eqn_key::Symbol, expr::Expr; modelmodule::Module)
```

Process the given expression in the context of the given module, create the Equation() instance for it, and add it to the model instance.

Usually there's no need to call this function directly. It is called during [`@initialize`](@ref).
