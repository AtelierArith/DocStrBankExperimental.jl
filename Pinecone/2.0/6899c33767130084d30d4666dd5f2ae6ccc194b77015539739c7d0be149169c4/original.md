create_index(ctx::PineconeContext, indexname::String, dimension::Int64; metric::String="cosine", pods::Int64=1, replicas::Int64=1, shards::Int64=1, podtype::String="p1")

Creates an index with a given PineconeContext, which can be accessed by a call to init(), the name of the index, and the number of dimensions.

This function returns a JSON blob as a string, or nothing if it failed. Do recommend using JSON3 to parse the blob.

# Example

```julia
context = Pinecone.init("abcd-123456-zyx", "us-west1-gcp")
result = Pinecone.create_index(context, testindexname, 10, metric="euclidean", replicas=2, shards=1)
```
