```
derivative_argument(dref::DerivativeRef)::GeneralVariableRef
```

微分演算子の入力である無限変数/微分参照（すなわち、微分の従属変数）を返します。

**例**

```julia-repl
julia> derivative_argument(dref) 
x(t)
```
