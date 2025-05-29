```
@NLconstraint(model::GenericModel, expr)
```

非線形式 `expr` で説明される制約を追加します。 [`@constraint`](@ref) も参照してください。

!!! compat
    このマクロは、従来の非線形インターフェースの一部です。 [非線形モデリング](@ref) に記載されている新しい非線形インターフェースの使用を検討してください。ほとんどの場合、`@NLconstraint` を [`@constraint`](@ref) に置き換えることができます。


## 例

```jldoctest
julia> model = Model();

julia> @variable(model, x)
x

julia> @NLconstraint(model, sin(x) <= 1)
sin(x) - 1.0 ≤ 0

julia> @NLconstraint(model, [i = 1:3], sin(i * x) <= 1 / i)
3-element Vector{NonlinearConstraintRef{ScalarShape}}:
 (sin(1.0 * x) - 1.0 / 1.0) - 0.0 ≤ 0
 (sin(2.0 * x) - 1.0 / 2.0) - 0.0 ≤ 0
 (sin(3.0 * x) - 1.0 / 3.0) - 0.0 ≤ 0
```
