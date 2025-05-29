```
check_belongs_to_model(con_ref::ConstraintRef, model::AbstractModel)
```

Throw `ConstraintNotOwned` if `owner_model(con_ref)` is not `model`.
