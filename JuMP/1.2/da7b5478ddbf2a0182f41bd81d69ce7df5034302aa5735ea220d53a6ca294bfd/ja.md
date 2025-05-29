```
SkewSymmetricMatrixSpace()
```

[`@variable`](@ref) マクロを使用して、変数の行列を歪対称に制約します。

## 例

```jldoctest; setup=:(model = Model())
@variable(model, Q[1:2, 1:2] in SkewSymmetricMatrixSpace())
```
