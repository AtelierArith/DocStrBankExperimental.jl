```
Words(tree)
```

Iterator for words in a sentence.

```jldoctest
julia> Words(tree"(S (NP (DT the) (N cat)) (VP (V ate)))") |> collect
3-element Array{Any,1}:
 "the"
 "cat"
 "ate"
```

# Arguments

  * `tree`: the tree to search

# Returns

  * `WordsIterator`: an iterator over tokens
