```
reset_uniquename!(str::String, counter=GLOBAL_NAME_COUNTER)
```

Reset [`uniquename`](@ref) counter for `str`.

`counter` is the `Dict{String,Int}` that counts how many times each name has been seen. The default is the same default global counter used by `uniquename`.
