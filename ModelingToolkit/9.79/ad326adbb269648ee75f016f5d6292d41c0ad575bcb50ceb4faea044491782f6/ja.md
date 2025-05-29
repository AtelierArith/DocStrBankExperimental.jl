```julia
open_loop(
    sys,
    ap::Union{Symbol, ModelingToolkit.AnalysisPoint};
    system_modifier
) -> Tuple{Any, Tuple{Any, Any}}

```

分析点 `ap` に `LoopTransferTransform` を適用し、`apply_transformation` の結果を返します。

# キーワード引数

  * `system_modifier`: 修正されたシステムを受け取り、必要なさらなる修正が行われた新しいシステムを返す関数。
