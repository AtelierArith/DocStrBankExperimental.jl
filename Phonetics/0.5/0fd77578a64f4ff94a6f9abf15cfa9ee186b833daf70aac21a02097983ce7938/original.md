```
upt(corpus, queries; [inCorpus=true])
```

Calculates the phonological uniqueness point (upt) the items in `queries` based on the items in `corpus`. If the items are expected to be in the corpus, this function will calculate the uniqueness point to be when a branch can be considered to only represent 1 word. If the items are not expected to be in the corpus, the uniqueness point will be taken to be the depth at which the tree can no longer be traversed.

# Parameters

  * **corpus** The items comprising the corpus to compare against when calculating   the uniqueness point of each query
  * **queries** The items for which to calculate the uniqueness point
  * **inLexicon** Whether the query items are expected to be in the corpus or not

# Returns

  * A `DataFrame` with the queries in the first column and the uniqueness points   in the second
