```
num_nonlinear_constraints(model::GenericModel)
```

`model`に関連付けられた非線形制約の数を返します。

!!! compat
    この関数は、従来の非線形インターフェースの一部です。[非線形モデリング](@ref)で文書化されている新しい非線形インターフェースの使用を検討してください。


この関数は、[`@NLconstraint`](@ref)および[`add_nonlinear_constraint`](@ref)を使用して追加された制約のみをカウントします。[`GenericNonlinearExpr`](@ref)制約はカウントしません。
