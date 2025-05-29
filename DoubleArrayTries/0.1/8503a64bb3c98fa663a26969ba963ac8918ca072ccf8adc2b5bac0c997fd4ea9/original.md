```
PredictiveSearch(dat::DoubleArrayTrie, key::AbstractString)
```

Return a iterable object that iterate through all string in the trie that has prefix of `prefix`. Each element is  be a tuple of id and the string (`Tuple{Int, String}`).
