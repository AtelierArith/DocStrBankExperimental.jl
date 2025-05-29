```
whoami(context::PineconeContext)
```

Returns JSON blob with information about your connection to Pinecone.

# Example

```julia-repl
julia> context = Pinecone.init("abcd-1234-zyxv", "us-west1-gcp")
Pinecone.whoami(context)
```
