```
@quickcheck qc [file_id::AbstractString="yyyy-mm-dd_HH-MM-SS"]
```

Check the properties specified in object `qc` of type [`Quickcheck`](@ref).

If `qc.serialize_fails` is `true`, serialize the failing cases to `JCheck_<file_id>.jchk`. Those can latter be analyzed using [`load`](@ref) and [`@getcases`](@ref).

# Note

If no argument `file_id` is passed, defaults to current time.
