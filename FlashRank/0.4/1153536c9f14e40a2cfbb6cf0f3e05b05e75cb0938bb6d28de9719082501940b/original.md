```
EmbedResult{T <: Real}
```

The result of embedding passages.

# Fields

  * `embeddings::AbstractArray{T}`: The embeddings of the passages. With property `embeddings` as column-major matrix of size `(batch_size, embedding_dimension)`.
  * `elapsed::Float64`: The time taken to embed the passages.
