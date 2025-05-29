```
get_trace_product(shadows::AbstractShadow...; O::Union{Nothing, MPO}=nothing)
```

複数のシャドウオブジェクトの積を計算し、そのトレースまたは期待値を返します。

`O` が `nothing` の場合、積のトレースを返します:     trace(shadow₁ * shadow₂ * ... * shadowₙ)。`O` が提供されると、次のように計算された期待値を返します:     get*expect*shadow(O, shadow₁ * shadow₂ * ... * shadowₙ)。

# 引数

  * `shadows...`: 可変数のシャドウオブジェクト。
  * `O::Union{Nothing, MPO}` (オプション): MPOオブザーバブル。

# 戻り値

`O` が `nothing` の場合は積のトレース、または `O` が提供された場合は期待値を返します。

# 例

```julia
result = get_trace_product(shadow1, shadow2, shadow3)
result_with_O = get_trace_product(shadow1, shadow2, shadow3; O=my_operator)
```
