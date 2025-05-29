```
Base.setproperty!(@nospecialize(ids::IDS), field::Symbol, value::AbstractArray; skip_non_coordinates::Bool=false, error_on_missing_coordinates::Bool=true)
```

Ensures coordinates are set before the data that depends on those coordinates.

If `skip_non_coordinates` is set, then fields that are not coordinates will be silently skipped.
