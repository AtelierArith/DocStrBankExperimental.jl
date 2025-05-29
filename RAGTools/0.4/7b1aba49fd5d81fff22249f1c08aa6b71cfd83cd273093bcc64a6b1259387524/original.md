```
CandidateChunks
```

A struct for storing references to chunks in the given index (identified by `index_id`)  called `positions` and `scores` holding the strength of similarity (=1 is the highest,  most similar). It's the result of the retrieval stage of RAG.

# Fields

  * `index_id::Symbol`: the id of the index from which the candidates are drawn
  * `positions::Vector{Int}`: the positions of the candidates in the index (ie, `5`

```
refers to the 5th chunk in the index - `chunks(index)[5]`)
```

  * `scores::Vector{Float32}`: the similarity scores of the candidates from the query (higher is better)
