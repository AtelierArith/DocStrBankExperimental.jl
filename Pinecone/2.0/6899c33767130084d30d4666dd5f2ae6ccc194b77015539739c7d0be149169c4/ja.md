create_index(ctx::PineconeContext, indexname::String, dimension::Int64; metric::String="cosine", pods::Int64=1, replicas::Int64=1, shards::Int64=1, podtype::String="p1")

指定されたPineconeContext、インデックスの名前、および次元数を使用してインデックスを作成します。

この関数は、失敗した場合は何も返さず、JSONのブロブを文字列として返します。ブロブを解析するためにJSON3の使用をお勧めします。

# 例

```julia
context = Pinecone.init("abcd-123456-zyx", "us-west1-gcp")
result = Pinecone.create_index(context, testindexname, 10, metric="euclidean", replicas=2, shards=1)
```
