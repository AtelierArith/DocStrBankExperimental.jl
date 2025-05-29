```julia
File(filename; second_in_pair = nothing)
```

For paired files a function taking as argument the filename of the first file in pair and returning the filename of the second file can be provided. For example one can use `replace`  or a dictionnary, e.g. `second_in_pair = f1 -> replace(f1, "_1" => "_2")`.
