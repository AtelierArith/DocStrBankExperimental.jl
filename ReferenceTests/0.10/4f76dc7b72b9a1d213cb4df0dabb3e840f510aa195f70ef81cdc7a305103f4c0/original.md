```
@io2str ex
```

Search and replace the placeholder `::IO` with a newly allocated `Base.IOBuffer` which is afterwards converted to a string and returned.

This macro allows a user to conveniently test text-based printing functionality that require an `IO` argument. A particularly common example of such would be a custom `Base.show` method.

# Examples

```julia-repl
julia> using ReferenceTests

julia> @io2str print(::IO, "Hello World")
"Hello World"

julia> @io2str show(IOContext(::IO, :limit=>true, :displaysize=>(10,10)), "text/plain", ones(5))
"5-element Array{Float64,1}:
 1.0
 1.0
 1.0
 1.0
 1.0"
```
