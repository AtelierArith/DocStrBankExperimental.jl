```
compile(s::String; force::Bool=false)
```

Compiles the library given by path `deps/s`. If `force` is false, `compile` first check whether  the binary product exists. If the binary product exists, return 2. Otherwise, `compile` tries to  compile the binary product, and returns 0 if successful; it return 1 otherwise. 
