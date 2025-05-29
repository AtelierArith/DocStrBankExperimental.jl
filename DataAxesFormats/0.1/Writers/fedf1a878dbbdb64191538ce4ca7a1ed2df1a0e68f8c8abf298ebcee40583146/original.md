```
delete_axis!(
    daf::DafWriter,
    axis::AbstractString;
    must_exist::Bool = true,
)::Nothing
```

Delete an `axis` from the `daf`. This will also delete any vector or matrix properties that are based on this axis.

If `must_exist` (the default), this first verifies the `axis` exists in the `daf`.
