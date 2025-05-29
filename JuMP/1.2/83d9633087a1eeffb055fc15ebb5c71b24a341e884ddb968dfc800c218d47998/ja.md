```
build_variable(_error::Function, variables, ::SymmetricMatrixSpace)
```

`MOI.Reals`で変数を作成する[`VariablesConstrainedOnCreation`](@ref)を返します。すなわち、作成後に制約がかけられない限り「自由」変数です。

この関数は、次のように[`@variable`](@ref)マクロによって使用されます：

```julia
@variable(model, Q[1:2, 1:2], Symmetric)
```
