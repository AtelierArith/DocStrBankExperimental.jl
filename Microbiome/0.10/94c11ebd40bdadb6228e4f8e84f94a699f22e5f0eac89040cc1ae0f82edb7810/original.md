```
unset!(as::AbstractSample, prop::Symbol)
```

Delete a metadata entry of sample `as` using the Symbol `prop`.  If you want an error to be thrown if the value does not exist, use [`delete!`](@ref).
