```
complement(set <: SBSet)
```

補集合を生成します

```julia julia> complement(@setbuild()) == @setbuild(Any) true

julia> ~@setbuild() == @setbuild(Any) true
```
