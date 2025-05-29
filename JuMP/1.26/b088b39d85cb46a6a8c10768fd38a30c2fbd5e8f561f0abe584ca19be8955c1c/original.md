```
add_constraint(
    model::GenericModel,
    con::AbstractConstraint,
    name::String= "",
)
```

This method should only be implemented by developers creating JuMP extensions. It should never be called by users of JuMP.
