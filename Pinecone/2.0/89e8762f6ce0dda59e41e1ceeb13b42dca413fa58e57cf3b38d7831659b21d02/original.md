```
upsert(ctx::PineconeContext, indexobj::PineconeIndex, vectors::Vector{PineconeVector}, namespace::String="")
```

upserts a Julia Vector of type PineconeVector using the given PineconeContext and PineconeIndex with an optional namespace (Defaults to not being applied to query if not passed.) On success returns a JSON blob as a String type, and nothing if it fails.  This function returns a JSON blob as a string, or nothing if it failed. Do recommend using JSON3 to parse the blob.

# Example

```julia-repl
julia> testvector = Pinecone.PineconeVector("testid", [0.3,0.11,0.3,0.3,0.3,0.3,0.3,0.3,0.4,0.3])
context = Pinecone.init("abcd-123456-zyx", "us-west1-gcp")
index = PineconeIndex("myindex")
result = Pinecone.upsert(context, index, [testvector], "testnamespace")
```
