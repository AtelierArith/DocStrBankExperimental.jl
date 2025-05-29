```
operator_parameter(dref::DerivativeRef)::GeneralVariableRef
```

微分演算子が作用している無限パラメータ参照を返します（すなわち、導関数の独立変数）。

**例**

```julia-repl
julia> operator_parameter(dref) 
t
```
