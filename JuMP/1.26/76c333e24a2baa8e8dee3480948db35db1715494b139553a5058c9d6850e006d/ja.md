```
all_nonlinear_constraints(model::GenericModel)
```

モデルに追加された順に、すべての非線形制約参照のベクターを返します。

!!! compat
    この関数は、従来の非線形インターフェースの一部です。 [非線形モデリング](@ref) に記載されている新しい非線形インターフェースの使用を検討してください。


この関数は、[`@NLconstraint`](@ref) および [`add_nonlinear_constraint`](@ref) を使用して追加された制約のみを返します。 [`GenericNonlinearExpr`](@ref) 制約は返しません。
