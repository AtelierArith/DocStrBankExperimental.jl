```
describe_index_stats(ctx::PineconeContext, indexobj::PineconeIndex)
```

特定のインデックスを説明するJSONブロブをString型で返します。失敗した場合は$nothing$を返します。

# 例

```julia
context = Pinecone.init("abcde-1234-zyxv", "us-west1-gcp")
index = PineconeIndex("my-index")
Pinecone.describe_index_stats(context, index)
"namespaces":{"test_namespace":{"vectorCount":1},"testnamespace":{"vectorCount":1},"":{"vectorCount":5}},"dimension":10}
```
