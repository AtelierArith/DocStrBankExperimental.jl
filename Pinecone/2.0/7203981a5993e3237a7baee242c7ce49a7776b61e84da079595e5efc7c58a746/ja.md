```
delete(ctx::PineconeContext, indexobj::PineconeIndex, ids::Array{String}, deleteall::Bool, namespace::String)
```

$$
ids
$$

でインデックスされたベクトルを削除します。 **警告:** deleteall=trueの場合、ベクトルの全体の名前空間が削除されます。

失敗した場合は、空のオブジェクトの$String$としてJSONブロブを返すか、何も返しません。

# 例

```julia-repl
julia> context = Pinecone.init("asdf-1234-zyxv", "us-west1-gcp")
index = PineconeIndex("my-index")
Pinecone.delete(context, index, ["deleteme1", "deleteme2"], false, "timnamespace")
{}
```
