```
download!(granule::Granule, folder=".")
```

Download the file associated with `granule` to the `folder`, from an http(s) location if it doesn't already exists locally.

Will require credentials (netrc) which can be set with [`netrc!`](@ref).
