```
ScheduleConstraint{T} <: Data where {T<:AbstractScheduleType}
```

A constraint that can be added as `Data`. `T <: AbstractScheduleType` denotes the constraint type.

## Fields

  * **`resource::{Union{<:Resource, Nothing}}`** is the resource type the constraint applies to if the node can have multiple resources as input/outputs.
  * **`value::TimeProfile`** is the constraint value, that is the limit that should not be violated.
  * **`flag::TimeProfile`** is a boolean value indicating if the constraint is active.
  * **`penalty::TimeProfile`** is the penalty for violating the constraint. If penalty is set to `Inf` it will be built as a hard constraint.
