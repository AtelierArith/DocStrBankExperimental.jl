```
SA[ elements ]
SA{T}[ elements ]
```

Create `SArray` literals using array construction syntax. The element type is inferred by promoting `elements` to a common type or set to `T` when `T` is provided explicitly.

# Examples:

  * `SA[1.0, 2.0]` creates a length-2 `SVector` of `Float64` elements.
  * `SA[1 2; 3 4]` creates a 2×2 `SMatrix` of `Int`s.
  * `SA[1 2]` creates a 1×2 `SMatrix` of `Int`s.
  * `SA{Float32}[1, 2]` creates a length-2 `SVector` of `Float32` elements.

A couple of helpful type aliases are also provided:

  * `SA_F64[1, 2]` creates a length-2 `SVector` of `Float64` elements
  * `SA_F32[1, 2]` creates a length-2 `SVector` of `Float32` elements
