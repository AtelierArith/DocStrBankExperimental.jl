```
solve(model::Model, analysistype::AbstractAnalysisType)::AbstractSolutionCache
```

弾性座屈および自由振動解析を実行するために使用される関数です。

!!! note
    この関数は非変異的であり、モデルの状態を更新しません。代わりに、結果を抽出するために使用できる解キャッシュオブジェクトを返します。

