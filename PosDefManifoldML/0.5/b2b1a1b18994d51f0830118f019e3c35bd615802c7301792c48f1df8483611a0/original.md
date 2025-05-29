```julia
CVres(s::String) =
     CVres(s, nothing, nothing, nothing, nothing, nothing,
           nothing, nothing, nothing, nothing, nothing, nothing)
```

Construct an instance of the CVres structure giving only the `.cvtype` field. All other fields are filled with `nothing`. This is useful to construct manually crval objects.
