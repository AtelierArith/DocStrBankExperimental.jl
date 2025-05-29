modelObjectFromAnother(base, pairs::Pair{Symbol,<:Any}...)

Use this function to create a new struct starting from an  existing one, except for a few specified changes.

# Examples

```julia-repl

julia> struct ExStr
       a::Float64
       vec::Tuple{Float64, Float64, Float64}
       end

julia> s = ExStr(3.0, (1.0,2.0,10.0))
ExStr(3.0, (1.0, 2.0, 10.0))

julia> s2 = modelObjectFromAnother(s, :vec => (2.0, 1.0, 5.0))
ExStr(3.0, (2.0, 1.0, 5.0))

julia> s3 = modelObjectFromAnother(s, :vec => (2.0, 1.0, 5.0), :a => 4.5)
ExStr(4.5, (2.0, 1.0, 5.0))
```
