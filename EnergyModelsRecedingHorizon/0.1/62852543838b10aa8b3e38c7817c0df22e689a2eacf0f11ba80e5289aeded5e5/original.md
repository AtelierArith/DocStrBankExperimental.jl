```
struct TypeFutureValue <: FutureValue
TypeFutureValue(element_type::Type{<:AbstractElement}, key::Symbol, val::Real)
```

A future value for a given nodal type and model key. It utilizes only the final value and directly adds it to the cost function for all instances of the given type.

## Fields

  * **`element::Type{<:AbstractElement}`** is the nodal type for which the future value applies.
  * **`val_dict::Dict{Symbol, Real}`** is a dictionary for including the variables provided as keys with a given value for calculating the future value. It is important to consider the unit of the value.

!!! info "Single variable"
    The field `val_dict` can also be provided as key and value input, if only a single variable should be restricted


!!! danger "Application of TypeFutureValue"
    `TypeFutureValue` assigns a future value to all instances of a given type. It should **never** be used on reference nodes. It should only be used on dynamic variables for other node types.

