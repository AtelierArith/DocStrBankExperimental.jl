```
whoami(context::PineconeContext)
```

Pineconeへの接続に関する情報を含むJSONブロブを返します。

# 例

```julia-repl
julia> context = Pinecone.init("abcd-1234-zyxv", "us-west1-gcp")
Pinecone.whoami(context)
```
