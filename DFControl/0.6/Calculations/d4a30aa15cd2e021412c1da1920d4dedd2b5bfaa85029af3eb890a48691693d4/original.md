```
set_flags!(c::Calculation, flags::Pair{Symbol, Any}...; print=true, force=false)
```

Sets multiple flags in one go. Flag validity and type are verified.

```
set_flags!(job::Job, calculations::Vector{<:Calculation}, flags::Pair{Symbol,<:Any}...; print=true)
set_flags!(job::Job, flags::Pair{Symbol,<:Any}...; print=true)
```

Sets the flags in the names to the flags specified. This only happens if the specified flags are valid for the names.
