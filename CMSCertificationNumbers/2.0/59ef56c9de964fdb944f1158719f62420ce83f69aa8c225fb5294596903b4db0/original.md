```
ccn([T::Type], s) -> CCN
```

Construct a CCN from input `s`.

# Arguments

  * `T::Type` (optional) - The type of the CCN. If no type is given, the best guess of the type will be made based on the format of the input `s` using [`infer_ccn_type`](@ref).
  * `s::Union{AbstractString,Integer}` - The input to parse to create the CCN.

# Return value

Returns a CCN of concrete type `T` if given, else the type will be inferred from format of `s`.
