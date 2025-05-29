```
graph_backend(graph::OptiGraph)
```

最適化グラフを最適化ツールにマッピングするために使用される中間バックエンドを返します。Plasmo.jl は現在、MathOptInterface.jl の最適化ツールへのバックエンドのみをサポートしていますが、将来のバージョンでは構造化バックエンドとしてGraphOptInterface.jlをサポートする予定です。
