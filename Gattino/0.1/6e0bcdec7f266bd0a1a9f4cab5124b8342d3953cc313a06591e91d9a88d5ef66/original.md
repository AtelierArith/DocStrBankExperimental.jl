```julia
`line` -> ::AbstractContext
```

`line`, `scatter`, and `hist` are all high-level plotting functions used to create a `Context` and display features  from a data structure using a single function call. `line` takes the same arguments as `line_plot!`, like the other plotting functions.      A `line` plot can be created using both a numberical and a non-numerical X.

```julia

```

###### methods

```julia
# from vectors
line(x::Vector{<:Any}, y::Vector{<:Any}, args ...; keyargs ...)
line(x::String, y::String, features::Dict{String, <:AbstractVector}, colors::Vector{String} = [randcolor() for e in 1:length(features)]; width::Int64 = 500, 
    height::Int64 = 500, keyargs ...)
line(features::Any, x::Any = names(features)[1], y::Any = names(features)[2], args ...; keyargs ...)
```
