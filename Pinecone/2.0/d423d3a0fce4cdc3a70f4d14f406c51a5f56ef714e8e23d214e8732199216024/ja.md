```
init(apikey::String, environment::String)
```

APIキーと特定の環境を使用してPinecone環境を初期化します。

これにより、query()やupsert()などの後続の呼び出しに使用するPineconeContextインスタンスが返されます。APIキーとインデックスのためのクラウド環境は、Pineconeコンソールで簡単に見つけることができます。失敗した場合は何も返しません。

# 例

```julia
using Pinecone
context = Pinecone.init("abcd-123456-zyx", "us-west1-gcp")
```
