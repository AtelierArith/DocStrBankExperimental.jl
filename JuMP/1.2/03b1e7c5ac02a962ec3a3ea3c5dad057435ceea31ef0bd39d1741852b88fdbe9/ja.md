```
build_variable(_error::Function, variables, ::SkewSymmetricMatrixSpace)
```

`MOI.Reals`で変数を作成する`VariablesConstrainedOnCreation`を返します。すなわち、作成後に制約がかけられない限り「自由」な変数です。

この関数は、次のように[`@variable`](@ref)マクロによって使用されます。

```julia
@variable(model, Q[1:2, 1:2] in SkewSymmetricMatrixSpace())
```
