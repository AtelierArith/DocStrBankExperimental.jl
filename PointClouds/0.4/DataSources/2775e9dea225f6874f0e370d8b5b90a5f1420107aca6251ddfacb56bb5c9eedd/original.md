```
LAS(t::PointCloudTile; kws...)
```

Load the point-cloud data of a `PointCloudTile`, downloading the file if necessary. Downloaded files are saved to the user’s cache directory as provided by [BaseDirs.jl](https://github.com/tecosaur/BaseDirs.jl) and loaded from there in the future. See [`Base.read(url, LAS)`](@ref Base.read(::IO, ::Type{PointClouds.LAS})) for keyword arguments.
