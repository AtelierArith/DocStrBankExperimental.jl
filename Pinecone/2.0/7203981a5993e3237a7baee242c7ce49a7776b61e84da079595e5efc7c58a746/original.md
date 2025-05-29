```
delete(ctx::PineconeContext, indexobj::PineconeIndex, ids::Array{String}, deleteall::Bool, namespace::String)
```

Deletes vectors indexed by $ids$.  **Warning:** The entire namespace for the vector will be deleted if deleteall=true

Returns JSON blob as $String$ of empty object or nothing if fails.

# Example

```julia-repl
julia> context = Pinecone.init("asdf-1234-zyxv", "us-west1-gcp")
index = PineconeIndex("my-index")
Pinecone.delete(context, index, ["deleteme1", "deleteme2"], false, "timnamespace")
{}
```
