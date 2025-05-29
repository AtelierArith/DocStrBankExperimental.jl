```
MultiCandidateChunks
```

A struct for storing references to multiple sets of chunks across different indices.  Each set of chunks is identified by an `index_id` in `index_ids`, with corresponding  `positions` in the index and `scores` indicating the strength of similarity.

This struct is useful for scenarios where candidates are drawn from multiple indices,  and there is a need to keep track of which candidates came from which index.

# Fields

  * `index_ids::Vector{Symbol}`: the ids of the indices from which the candidates are drawn
  * `positions::Vector{TP}`: the positions of the candidates in their respective indices
  * `scores::Vector{TD}`: the similarity scores of the candidates from the query
