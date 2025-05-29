```
delete!(commp::CommunityProfile, sample::AbstractString, prop::Symbol)
```

Delete a metadata entry in `sample` from CommunityProfile `commp` using the Symbol `prop` if it exists, or throw an error otherwise. If you don't want an error to be thrown if the value does not exist, use [`unset!`](@ref).
