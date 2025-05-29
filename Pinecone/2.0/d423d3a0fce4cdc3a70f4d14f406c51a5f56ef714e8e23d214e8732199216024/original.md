```
init(apikey::String, environment::String)
```

Initialize the Pinecone environment using your API Key and a specific environment.

This returns a PineconeContext instance which you'll use for subsequent calls such as query() and upsert(). Your API Key and the cloud environment for your indexes are easily found in the Pinecone console. On failure returns nothing.

# Example

```julia
using Pinecone
context = Pinecone.init("abcd-123456-zyx", "us-west1-gcp")
```
