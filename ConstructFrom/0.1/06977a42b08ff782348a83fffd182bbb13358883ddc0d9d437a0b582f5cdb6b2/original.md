```
construct_from(args...; kwargs...)
```

Construct an object without spelling out its type if the type can be inferred from context.

# Examples

```julia-repl
julia> vec::Vector{Vector{Int}} = construct_from(undef, 3);

julia> vec
3-element Vector{Vector{Int64}}:
 #undef
 #undef
 #undef
```
