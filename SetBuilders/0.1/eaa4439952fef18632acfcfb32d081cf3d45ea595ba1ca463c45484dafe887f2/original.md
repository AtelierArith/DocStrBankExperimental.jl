```
complement(set <: SBSet)
```

generates a complement set

```julia julia> complement(@setbuild()) == @setbuild(Any) true

julia> ~@setbuild() == @setbuild(Any) true
