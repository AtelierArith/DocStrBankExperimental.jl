```julia
interpolate!(mdcomp::Component{:div}, components::Component{<:Any} ...; keyargs ...) -> ::Nothing
interpolate!(comp::Component{:div}, fillfuncs::Pair{String, <:Any} ...) -> ::Nothing
```

Interpolates markdown inside the `:text` of a `div` (typically created using `tmd`).  The `Component{<:Any}` and key-word argument dispatch will interpolate in-line code blocks, as well  as values with a `%` before them. The latter function will take a series of strings paired with functions. 

The functions will be passed the `String` of a code block, the return is another `String` – the result.
