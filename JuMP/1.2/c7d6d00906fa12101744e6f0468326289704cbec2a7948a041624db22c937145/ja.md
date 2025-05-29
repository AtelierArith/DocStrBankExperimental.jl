```
build_variable(_error::Function, variables, ::PSDCone)
```

正定半定であることを制約とする形状 [`SymmetricMatrixShape`](@ref) の `VariablesConstrainedOnCreation` を返します。

この関数は、次のように [`@variable`](@ref) マクロによって使用されます：

```julia
@variable(model, Q[1:2, 1:2], PSD)
```
