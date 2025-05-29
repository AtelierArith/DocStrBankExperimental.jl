```
load_object(filename)
```

JLD2ファイル`filename`から唯一の利用可能なオブジェクトを返します（保存されたオブジェクト名は重要ではありません）。ファイルに複数のオブジェクトが含まれているか、オブジェクトがない場合、関数は`ArgumentError`をスローします。

複数のオブジェクトを読み込むには、[`@load`](@ref)マクロ、[`jldopen`](@ref)またはFileIO APIを使用してください。

# 例

JLD2ファイルexample.jld2から唯一のオブジェクトを読み込むには：

```julia
hello = "world"
save_object("example.jld2", hello)
hello_loaded = load_object("example.jld2")
```
