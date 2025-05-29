```
list_indexes(context::PineconeContext)
```

Returns a JSON array listing indexes for a given account, which is indicated by the PineconeContext instance passed in.

# Example

```julia-repl
julia> context = Pinecone.init("asdf-1234-zyxv", "us-west1-gcp")
Pinecone.list_indexes(context)
["example-index", "filter-example"]
```
