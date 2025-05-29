```
set!(as::AbstractSample, prop::Symbol, val)
```

Update or insert a value `val` to the metadata of sample `as` using a Symbol `prop`.  If you want an error to be thrown if the value already exists, use [`insert!`](@ref).
