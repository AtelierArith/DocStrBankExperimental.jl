```
POS(tree)
```

Iterator for part-of-speech tagged words.

```jldoctest
julia> POS(tree"(S (NP (DT the) (N cat)) (VP (V ate)))") |> collect
3-element Array{Any,1}:
 ("DT", "the")
 ("N", "cat")
 ("V", "ate")
```

# Arguments

  * `tree`: the tree to search

# Returns

  * `POSIterator`- a lazy iterator over (POS, token) pairs
