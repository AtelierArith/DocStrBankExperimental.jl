```
struct FreeVibrationAnalysis <: AbstractAnalysisType
```

自由振動解析を表す型です。

自由振動解析を実行するには、次のコマンドを使用します。

```julia
solution = solve(model, FreeVibrationAnalysis())
```
