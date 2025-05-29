```
set!(commp::CommunityProfile, sample::AbstractString, prop::Symbol, val)
set!(commp::CommunityProfile, sample::AbstractString, md::Union{AbstractDict, NamedTuple})
```

Update or insert a value `val` to the metadata of `sample` in the CommunityProfile `commp` using a Symbol `prop`.  If you want an error to be thrown if the value already exists, use [`insert!`](@ref).

Can also pass a Dictionary or NamedTuple containing key=> value pairs, all of which will be `set!`.
