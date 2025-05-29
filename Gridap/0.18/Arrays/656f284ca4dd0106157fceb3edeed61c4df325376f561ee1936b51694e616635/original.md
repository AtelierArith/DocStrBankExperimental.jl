```
evaluate(f,x...)
```

evaluates the mapping `f` at the arguments in `x` by creating a temporary cache internally. This functions is equivalent to

```jl
cache = return_cache(f,x...)
evaluate!(cache,f,x...)
```
