```
decode(dat::DoubleArrayTrie, i::Int)
```

Take an id `i` and return a corresponding string in the trie. If `i <= 0 || i > length(dat)`, it will always  return `nothing`.
