```
CommonPrefixSearch(dat::DoubleArrayTrie, key::AbstractString)
```

Return a iterable object that iterate through all string in the trie that has common prefix with `key`. Each element is  a tuple of id and the string (`Tuple{Int, String}`).
