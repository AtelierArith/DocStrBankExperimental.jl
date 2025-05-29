```julia
function sameParams(𝒀        :: TFobjectsVector,
                    funcname :: String) =
```

すべてのオブジェクトが同じ `bandwidth`、`nonlinear`、`fsmoothing` および `tsmoothing` フィールドを持っている場合は true を返し、そうでない場合はすべてのオブジェクトで同一でない最初のフィールドを指摘するエラーメッセージを印刷し、`Nothing` を返します。このメソッドはすべての [TFobjectsVector](@ref) タイプ、すなわち [TFAnalyticSignalVector](@ref)、[TFAmplitudeVector](@ref) および [TFPhaseVector](@ref) に適用されます。

`funcname` は前のメソッドと同じ意味を持ちます。
