```
upsert(ctx::PineconeContext, indexobj::PineconeIndex, vectors::Vector{PineconeVector}, namespace::String="")
```

指定されたPineconeContextとPineconeIndexを使用して、オプションの名前空間（指定されていない場合はクエリに適用されないデフォルト）でJuliaのPineconeVector型のベクターをアップサートします。成功した場合は、String型のJSONブロブを返し、失敗した場合は何も返しません。この関数は、文字列としてJSONブロブを返すか、失敗した場合は何も返しません。JSON3を使用してブロブを解析することをお勧めします。

# 例

```julia-repl
julia> testvector = Pinecone.PineconeVector("testid", [0.3,0.11,0.3,0.3,0.3,0.3,0.3,0.3,0.4,0.3])
context = Pinecone.init("abcd-123456-zyx", "us-west1-gcp")
index = PineconeIndex("myindex")
result = Pinecone.upsert(context, index, [testvector], "testnamespace")
```
