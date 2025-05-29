```
struct ConstraintNotOwned{C <: ConstraintRef} <: Exception
    constraint_ref::C
end
```

The constraint `constraint_ref` was used in a model different to `owner_model(constraint_ref)`.
