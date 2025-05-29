```
save_object(filename, x)
```

オブジェクト `x` を `filename` の新しい JLD2 ファイルに保存します。このパスにファイルが存在する場合は、上書きされます。

JLD2 形式ではすべてのオブジェクトに名前が必要なため、オブジェクトは `single_stored_object` として保存されます。複数のオブジェクトを保存したい場合は、[`@save`](@ref) マクロ、[`jldopen`](@ref) または FileIO API を使用してください。

# 例

文字列 `hello` を JLD2 ファイル example.jld2 に保存するには：

```julia
hello = "world"
save_object("example.jld2", hello)
```
