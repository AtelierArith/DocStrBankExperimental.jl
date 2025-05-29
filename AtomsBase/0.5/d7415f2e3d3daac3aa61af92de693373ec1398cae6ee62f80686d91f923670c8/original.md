```
AbstractSystem(system::AbstractSystem; kwargs...)
```

Update constructor. Construct a new system where one or more properties are changed, which are given as `kwargs`. A subtype of `AbstractSystem` is returned, by default a `FlexibleSystem`, but depending on the type of the passed system this might differ.

Supported `kwargs` include `particles`, `atoms`, `cell_vectors` and `periodicity` as well as user-specific custom properties.

# Examples

Change the bounding box and the atoms of the passed system

```julia-repl
julia> AbstractSystem(system; cell_vectors= ..., atoms = ... )
```
