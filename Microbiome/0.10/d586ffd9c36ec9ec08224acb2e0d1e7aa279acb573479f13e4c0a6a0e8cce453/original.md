```
delete!(as::AbstractSample, prop::Symbol)
```

Delete a metadata entry of sample `as` using the Symbol `prop` if it exists, or throw an error otherwise. If you don't want an error to be thrown if the value does not exist, use [`unset!`](@ref).
