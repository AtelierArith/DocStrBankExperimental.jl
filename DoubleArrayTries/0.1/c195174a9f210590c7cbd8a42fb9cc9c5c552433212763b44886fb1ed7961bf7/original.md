```
DoubleArrayTrie(keys::AbstractVector{<:AbstractString}; bin_mode = true)
```

Accept a list of strings and build the double array trie. If `keys` is a `Vector`, it will be modified by `sort!` and  `unique!`. Set `bin_mode = true` allow `' '` as a character, this is needed for non-ascii strings.
