```
parameter_list(dref::DerivativeRef)::Vector{GeneralVariableRef}
```

`dref`が依存しているパラメータ参照のベクターを返します。これは主に内部メソッドであり、[`parameter_refs`](@ref parameter_refs(::DerivativeRef))が推奨されるユーザー関数として意図されています。
