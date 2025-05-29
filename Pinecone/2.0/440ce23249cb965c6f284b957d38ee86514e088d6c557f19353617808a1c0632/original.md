```
describe_index_stats(ctx::PineconeContext, indexobj::PineconeIndex)
```

Returns JSON blob as a String type describing a particular index.  Returns $nothing$ on failure.

# Example

```julia
context = Pinecone.init("abcde-1234-zyxv", "us-west1-gcp")
index = PineconeIndex("my-index")
Pinecone.describe_index_stats(context, index)
"namespaces":{"test_namespace":{"vectorCount":1},"testnamespace":{"vectorCount":1},"":{"vectorCount":5}},"dimension":10}
```
