# PlutoStaticHTML.jl

2つのノートブックを迅速に構築するには（すべてのコードを評価し、出力をHTMLに変換する）、次のようにします：

```
julia> dir = joinpath("posts", "notebooks");

julia> files = ["notebook1.jl", "notebook2.jl"];

julia> build_notebooks(BuildOptions(dir), files)
```

すべてのノートブックを構築するには、次のようにします：

```
julia> build_notebooks(BuildOptions(dir))
```

完全なドキュメントについては、https://rikhuijzer.github.io/PlutoStaticHTML.jl/dev/ を参照してください。
