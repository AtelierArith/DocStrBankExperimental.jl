```
delete_index(ctx::PineconeContext, indexobj::PineconeIndex)
```

Deletes an index, returns true on successful response from Pinecone backend.

This delets a given Pinecone index, note that this is an asynch call and doesn't guarantee that on return that the index is actually deleted (yet).

# Example

```julia
Pinecone.delete_index(context, Pinecone.Index("index-to-delete"))
```
