```
struct ElasticBucklingAnalysis <: AbstractAnalysisType
```

弾性座屈解析を表す型です。

弾性座屈解析を実行するには、次のコマンドを使用します：

```julia
solution = solve(model, ElasticBucklingAnalysis())
```
