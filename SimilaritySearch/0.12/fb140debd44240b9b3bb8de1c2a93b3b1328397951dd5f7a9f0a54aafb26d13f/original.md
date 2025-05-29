```
find_neighborhood(copy_, index::SearchGraph{T}, context, item; hints=index.hints)
```

Searches for `item` neighborhood in the index, i.e., if `item` were in the index whose items should be its neighbors (intenal function). The `copy_` function forces to control how the returned KnnResult object is handled because it uses a cache result set from the given context. 

# Arguments

  * `copy_`: A copying function, it controls what is retrieved by the function.
  * `index`: The search index.
  * `item`: The item to be inserted.
  * `context`: context, neighborhood, and cache objects to be used
  * `hints`: Search hints
