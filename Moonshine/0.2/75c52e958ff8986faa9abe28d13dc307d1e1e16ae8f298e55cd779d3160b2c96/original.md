```
sequences(genealogy[, e])
sequences(genealogy[, vs])
```

Sequences of a genealogy. If an edge is specified, return the sequences associated with the vertices incident to that edge. If an iterable of vertices is specified, return the sequences associated with these vertices.

See also [`sequence`](@ref) to get the sequence associated with a vertex.

# Implementation

Custom types only need to implement `sequences(::T)`.

# Methods

```julia
sequences(genealogy, vs)
```

defined at [`packages/Moonshine/7JVTP/src/Genealogy.jl:147`](file:///Users/atelierarith/.julia/packages/Moonshine/7JVTP/src/Genealogy.jl).

```julia
sequences(genealogy, e)
```

defined at [`packages/Moonshine/7JVTP/src/Genealogy.jl:149`](file:///Users/atelierarith/.julia/packages/Moonshine/7JVTP/src/Genealogy.jl).

```julia
sequences(arg)
sequences(tree)
```

defined at [`packages/Moonshine/7JVTP/src/genealogy_common.jl:31`](file:///Users/atelierarith/.julia/packages/Moonshine/7JVTP/src/genealogy_common.jl).
