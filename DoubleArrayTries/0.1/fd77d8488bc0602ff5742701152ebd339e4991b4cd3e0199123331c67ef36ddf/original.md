```
lookup(dat::DoubleArrayTrie, key::S) where S <: Union{AbstractString, AbstractVector{UInt8}}
```

Lookup the `key` in the trie, return a unique id where `0 <= id <= length(dat)`. If the id is 0, it means the `key` does  not present in the trie.
