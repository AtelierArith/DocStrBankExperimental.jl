```
outputs(v)
```

Return an Array of vertices for which the given vertex is input to.

# Examples

```jldoctest
julia> using NaiveNASlib

julia> iv = inputvertex("in", 3);

julia> cv = invariantvertex(identity, iv);

julia> outputs(iv)
1-element Vector{NaiveNASlib.AbstractVertex}:
 MutationVertex(CompVertex(identity, inputs=[in], outputs=[]), NaiveNASlib.SizeInvariant()) 
```
