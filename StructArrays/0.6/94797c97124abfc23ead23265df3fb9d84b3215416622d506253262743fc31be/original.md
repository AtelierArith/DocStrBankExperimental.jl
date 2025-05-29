```
collect_structarray(itr; initializer = default_initializer)
```

Collects `itr` into a `StructArray`. The user can optionally pass a `initializer`, that is to say a function `(S, d) -> v` that associates to a type and a size an array of eltype `S` and size `d`. By default `initializer` returns a `StructArray` of `Array` but custom array types may be used.
