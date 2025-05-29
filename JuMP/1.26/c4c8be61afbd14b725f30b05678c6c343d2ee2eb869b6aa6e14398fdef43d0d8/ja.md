```
check_belongs_to_model(con_ref::ConstraintRef, model::AbstractModel)
```

`owner_model(con_ref)` が `model` でない場合、`ConstraintNotOwned` をスローします。
