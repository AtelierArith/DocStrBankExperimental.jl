```
@inside <expr>
```

Simple macro to automate efficient loops over cells excluding ghosts. For example,

```
@inside p[I] = sum(loc(0,I))
```

becomes

```
@loop p[I] = sum(loc(0,I)) over I ∈ inside(p)
```

See [`@loop`](@ref).
