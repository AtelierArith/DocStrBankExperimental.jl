```
fetch(ctx::PineconeContext, indexobj::PineconeIndex, ids::Array{String}, namespace::String)
```

ベクトルのIDに基づいてベクトルを取得します。これは、特定の名前空間に対して提供された$ids$配列として与えられます。名前空間はオプションであり、提供されない場合は、名前空間によるクエリ結果のフィルタリングに使用しないことがデフォルトとなります。失敗した場合は、$String$として以下に示すJSONブロブを返すか、$nothing$を返します。

# 例

```julia-repl
julia> context = Pinecone.init("asdf-1234-zyxv", "us-west1-gcp")
index = PineconeIndex("my-index")
Pinecone.fetch(context, index, ["testid", "testid2"], "testnamespace")
{"vectors":{"testid":{"id":"testid","values":[0.3,0.11,0.3,0.3,0.3,0.3,0.3,0.3,0.4,0.3],"metadata":{"year":2019,"genre":"documentary"}},
"testid2":{"id":"testid2","values":[0.3,0.11,0.3,0.3,0.3,0.3,0.3,0.3,0.4,0.3],"metadata":{"genre":"documentary","year":2019}}},"namespace":"testnamespace"}
```
