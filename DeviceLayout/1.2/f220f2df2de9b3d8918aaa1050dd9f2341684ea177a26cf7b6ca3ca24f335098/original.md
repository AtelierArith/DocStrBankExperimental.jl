```
reset_uniquename!(counter=GLOBAL_NAME_COUNTER)
```

Reset [`uniquename`](@ref) counters for all strings.

`counter` is the `Dict{String,Int}` that counts how many times each name has been seen. The default is the same default global counter used by `uniquename`.
