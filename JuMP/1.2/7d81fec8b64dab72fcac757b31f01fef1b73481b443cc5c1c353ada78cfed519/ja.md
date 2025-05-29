```
SymmetricMatrixSpace()
```

[`@variable`](@ref) マクロを使用して、変数の行列を対称に制約します。

## 例

```jldoctest; setup=:(model = Model())
julia> @variable(model, Q[1:2, 1:2] in SymmetricMatrixSpace())
2×2 LinearAlgebra.Symmetric{VariableRef,Array{VariableRef,2}}:
 Q[1,1]  Q[1,2]
 Q[1,2]  Q[2,2]
```
