```
b::TraceTransformDSLProgram = inverse(a::TraceTransformDSLProgram)
```

[Trace Transform DSL](@ref)を使用して構築された全単射の逆を取得します。

逆は、[`pair_bijections!`](@ref)または[`is_involution!`](@ref)を介して全単射に関連付けられている必要があります。
