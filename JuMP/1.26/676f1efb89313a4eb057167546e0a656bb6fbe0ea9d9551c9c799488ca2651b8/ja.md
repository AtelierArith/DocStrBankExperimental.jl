```
SkewSymmetricMatrixSpace()
```

[`@variable`](@ref) マクロを使用して、変数の行列を反対称に制約します。

## 例

```jldoctest
julia> model = Model();

julia> @variable(model, Q[1:2, 1:2] in SkewSymmetricMatrixSpace())
2×2 Matrix{AffExpr}:
 0        Q[1,2]
 -Q[1,2]  0
```
