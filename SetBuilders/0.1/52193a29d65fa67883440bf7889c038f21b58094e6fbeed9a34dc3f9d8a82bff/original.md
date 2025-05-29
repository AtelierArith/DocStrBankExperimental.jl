```
SBSet - Type
```

The `SBSet` type is the supertype of all SetBuilders set types.

# Examples

```julia-repl
julia> I = @setbuild(Integer)
TypeSet(Integer)

julia> I isa SBSet
true
```
