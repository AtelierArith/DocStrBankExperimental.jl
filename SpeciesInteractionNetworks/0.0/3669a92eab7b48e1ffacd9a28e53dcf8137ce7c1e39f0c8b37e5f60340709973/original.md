```
interactions(N::SpeciesInteractionNetwork)
```

Returns a vector of all interactions in the network.

Each interactions is returned an un-named tuple of three elements: the source, the destination, and the value. For a binary network, for example, an interaction from `:a` to `:b` will be represented as `(:a,:b,true)`. The type of the tuple that is returned is given by `eltype(N)`, and is the same as the output of using iteration on a network.

Note that this method is substantially faster and more memory-efficient than using iteration (`int for int in N`), for reasons related to the indexing of non-zero interactions in the underlying data structure of the network.
