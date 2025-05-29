```
prescribeddofs(uebc::F1, u::F2) where {F1<:AbstractField,  F2<:AbstractField}
```

Find which degrees of freedom are prescribed. `uebc` = field which defines the constraints (is the dof fixed and to which value), `u` = field which does not have the constraints applied, and serves as the source of equation numbers; `uebc` and `u` may be one and the same field.
