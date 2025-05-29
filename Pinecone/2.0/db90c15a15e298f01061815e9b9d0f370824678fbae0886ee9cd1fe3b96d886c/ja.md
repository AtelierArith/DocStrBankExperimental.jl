```julia
query(ctx::PineconeContext, indexobj::PineconeIndex, queries::Vector{PineconeVector}, topk::Int64=10, namespace::String="", includevalues::Bool=false, includemeta::Bool=false, filter::Dict{String, Any}=Dict{String,Any}())

与えられたコンテキストを使用してインデックスをクエリし、渡された$queries$に一致するものを取得します。クエリされる$PineconeVector$は、上記で説明した単純な$PineconeVector$です。$queries$パラメータには$Vector{Vector{<:AbstractFloat}}$を受け取る別のバージョンの$query()$もあります。機能的には同等です。成功した場合は結果を含む$String$としてJSONブロブを返し、失敗した場合は$nothing$を返します。

topkはオプションのパラメータで、指定されていない場合はデフォルトで10になります。ブロブを解析するためにJSON3の使用をお勧めします。

# 例

```

julia-repl julia> testdict = Dict{String, Any}("genre"=>"documentary", "year"=>2019); julia> pinecone*context = Pinecone.init("abcdef-1234-zyxv", "us-west1-gcp") abcdef-1234-zyxv / us-west1-gcp / 1c9c2f3 julia> pinecone*index = Pinecone.Index("filter-example"); julia> testvector = Pinecone.PineconeVector("testid", [0.3,0.11,0.3,0.3,0.3,0.3,0.3,0.3,0.4,0.3], testdict) PineconeVector is id: testid values: [0.3, 0.11, 0.3, 0.3, 0.3, 0.3, 0.3, 0.3, 0.4, 0.3]meta: Dict{String, Any}("genre" => "documentary", "year" => 2019) julia> Pinecone.query(pinecone*context, pinecone*index, [testvector], 4) "{"results":[{"matches":[{"id":"testid","score":3.98966023e-07,"values":[0.3,0.11,0.3,0.3,0.3,0.3,0.3,0.3,0.4,0.3]},{"id":"C","score":0.0461001098,"values":[0.3,0.3,0.3,0.3,0.3,0.3,0.3,0.3,0.3,0.3]} ],"namespace":""}]}" ```
