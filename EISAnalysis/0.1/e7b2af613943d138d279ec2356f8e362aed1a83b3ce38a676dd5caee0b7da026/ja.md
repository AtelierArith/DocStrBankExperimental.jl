```
get_params(a::Union{CircuitElement,Circuit})
```

回路内の要素のパラメータを取得します。

# 属性

  * `a::Union{CircuitElement,Circuit}`: 回路または回路要素

# 例

```julia
using EISAnalysis
eval(initialize())
randles_circuit = 0.23r-(r-0.025wo^80)/0.2q
get_params(randles_circuit)

# 出力

4-element Vector{Any}:
 0.23
 1.0
  (0.025, 80.0)
  (0.2, 0.8)
```
