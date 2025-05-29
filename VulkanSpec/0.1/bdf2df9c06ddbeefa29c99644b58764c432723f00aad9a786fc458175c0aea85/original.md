Parameter requirement. Applies both to struct members and function parameters.

Requirement types: 

  * `OPTIONAL`: may have its default zero (or nullptr) value, acting as a sentinel value (similar to `Nothing` in Julia).
  * `REQUIRED`: must be provided, no sentinel value is allowed.
  * `POINTER_OPTIONAL`: is a pointer which may be null, but must have valid elements if provided.
  * `POINTER_REQUIRED`: must be a valid pointer, but its elements are optional (e.g. are allowed to be sentinel values).
  * `POINTER_FULLY_OPTIONAL`: may be null, or a pointer with optional elements (e.g. are allowed to be sentinel values).

```julia
primitive type PARAM_REQUIREMENT <: Enum{Int32} 32
```
