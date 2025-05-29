```
insert!(commp::CommunityProfile, sample::AbstractString, prop::Symbol, val)
```

Insert a value `val` to the metadata of `sample` in a CommunityProfile `commp` using a Symbol `prop`,  and it will throw an error if `prop` exists.  If you don't want an error to be thrown if the value exists, use [`set!`](@ref).
