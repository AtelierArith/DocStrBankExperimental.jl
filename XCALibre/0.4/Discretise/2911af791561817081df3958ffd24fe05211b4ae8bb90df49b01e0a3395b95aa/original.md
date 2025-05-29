```
struct Periodic{I,V} <: AbstractPhysicalConstraint
    ID::I
    value::V
end
```

Periodic boundary condition model.

### Fields

  * 'ID' – Boundary ID
  * `value` – tuple containing information needed to apply this boundary
