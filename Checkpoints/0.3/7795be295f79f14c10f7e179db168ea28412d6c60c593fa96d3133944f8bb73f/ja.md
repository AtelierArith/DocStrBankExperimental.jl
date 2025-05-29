```
index_checkpoint_files(dir)
```

`dir`内にあるチェックポイントによって出力されたすべてのファイルのインデックスを構築します。このインデックスは、チェックポイント*名、チェックポイント*パス、タグなどを示します。記録される内容の完全な情報については[`IndexEntry`](@ref)を参照してください。

便利なことに、`Vector{IndexEntry}`は有効な[Tables.jl Table][1]です。つまり、`DataFrame(index_checkpoint_files(dir))`を実行すると、扱いやすい[DataFrame][2]が得られます。

また、直接操作することもできます。たとえば、`model="Stage1"`というタグを持つ`forecasts`のすべてのチェックポイントファイルを取得したい場合は、次のようになります。

```julia
[checkpoint_path(x) for x in index_checkpoint_files(dir) if x.checkpoint_name=="forecast" && x.model=="Stage1"]
```

1: https://github.com/JuliaData/Tables.jl 2: https://github.com/JuliaData/DataFrames.jl
