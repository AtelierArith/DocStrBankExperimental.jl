```
fetch(ctx::PineconeContext, indexobj::PineconeIndex, ids::Array{String}, namespace::String)
```

Fetches vectors based on the vector ids for each vector, provided as the $ids$ array for a given namespace.  . Note that namespace is optional, and if not provided defaults to not using it to filter query results by namespace. Returns JSON blob as $String$ show below, or $nothing$ on failure.

# Example

```julia-repl
julia> context = Pinecone.init("asdf-1234-zyxv", "us-west1-gcp")
index = PineconeIndex("my-index")
Pinecone.fetch(context, index, ["testid", "testid2"], "testnamespace")
{"vectors":{"testid":{"id":"testid","values":[0.3,0.11,0.3,0.3,0.3,0.3,0.3,0.3,0.4,0.3],"metadata":{"year":2019,"genre":"documentary"}},
"testid2":{"id":"testid2","values":[0.3,0.11,0.3,0.3,0.3,0.3,0.3,0.3,0.4,0.3],"metadata":{"genre":"documentary","year":2019}}},"namespace":"testnamespace"}
```
