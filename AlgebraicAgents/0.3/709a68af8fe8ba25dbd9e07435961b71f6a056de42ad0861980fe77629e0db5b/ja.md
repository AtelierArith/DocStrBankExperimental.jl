```
run_graphviz(io::IO, graph::AbstractString; prog::Symbol=:dot, format::String="svg")
run_graphviz(path::AbstractString, graph::AbstractString; prog::Symbol=:dot, format::String="svg")
```

グラフをレンダリングするためにGraphvizプログラムを実行し、結果を`io`にストリームします。

これには、`prog`（例：`dot`）がパスに存在する必要があります（https://graphviz.orgを参照）または、`Graphviz_jll`パッケージがインストールされ、関数を呼び出す前にロードされている必要があります。

エージェント階層のGraphviz配線図を取得するには、[`wiring_diagram`](@ref)を参照してください。
