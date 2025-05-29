```
spinrange = SpinRange(range)
```

SpinRange構造体。これはAbstractSpinSpanから継承された特殊な型で、特定の範囲とスピンの数を選択するために使用されます。

# 引数

  * `range`: (`::AbstractVector`) スピンID。この引数はRange、Vector、またはBitVectorであることができます。

# 戻り値

  * `spinrange`: (`::SpinRange`) SpinRange構造体

# 例

```julia-repl
julia> spinrange = SpinRange(1:10)
julia> spinrange = SpinRange([1, 3, 5, 7])
julia> spinrange = SpinRange(obj.x .> 0)
```
