```
mutable struct KeplerGLMap 
    datasets::Vector{AbstractKeplerGLData}
    config::Dict{Symbol, Any}
    info::Dict{Symbol, Any}
    window::Dict{Symbol, Any}
end
```

Type that contains all the information to render a map.  `config` and `info` are of the same structure as the map JSON  serialization that Kepler.gl uses internally. `datasets` are instances of [`AbstractKeplerGLData`](@ref) that contain the data that the layers draw from.  `window` is additional information not used by Kepler.gl that contains information on window size, whether the map should be centered, and so on. 
