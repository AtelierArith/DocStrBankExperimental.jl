```julia
mount(fpair::Pair{String, String}) -> ::Route{Connection}/::Vector{Route{Connection}}
```

`mount` will create a route that serves a file or a all files in a directory.  The first part of `fpair` is the target route path, e.g. `/` would be home. If  the provided path is as directory, the Function will return a `Vector{AbstractRoute}`. For  a single file, this will be a route.

```example
module MyServer
using Toolips

logger = Toolips.Logger()

filemount::Route{Connection} = mount("/" => "templates/home.html")

dirmount::Vector{<:AbstractRoute} = mount("/files" => "public")

export filemount, dirmount, logger
end
```
