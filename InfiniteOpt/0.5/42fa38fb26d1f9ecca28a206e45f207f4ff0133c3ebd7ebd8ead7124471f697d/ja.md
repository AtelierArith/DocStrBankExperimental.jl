```
parameter_list(fref::ParameterFunctionRef)::Vector{GeneralVariableRef}
```

`fref`が依存しているパラメータ参照のベクターを返します。これは主に内部メソッドであり、[`parameter_refs`](@ref parameter_refs(::ParameterFunctionRef))が推奨されるユーザ関数として意図されています。
