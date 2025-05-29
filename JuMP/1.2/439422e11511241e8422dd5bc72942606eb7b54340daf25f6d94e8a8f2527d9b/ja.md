```
struct ConstraintNotOwned{C <: ConstraintRef} <: Exception
    constraint_ref::C
end
```

制約 `constraint_ref` は `owner_model(constraint_ref)` とは異なるモデルで使用されました。
