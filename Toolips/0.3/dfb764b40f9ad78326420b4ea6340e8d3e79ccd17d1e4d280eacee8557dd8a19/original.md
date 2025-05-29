```julia
abstract type AbstractRoute
```

An `AbstractRoute` holds a `path`, a target which navigates the user throughout the webpage,  as well as some way to generate that page. Typically, these are created using `route`, though this  might not always be the case. The canonical route provided by `Toolips` is `Route{<:Any}`.

  * See also: `route`, `route!`, `Connection`, `AbstractConnection`
