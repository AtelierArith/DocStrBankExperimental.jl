```
parameter_list(vref::InfiniteVariableRef)::Vector{GeneralVariableRef}
```

`vref` が依存しているパラメータ参照のベクターを返します。これは主に内部メソッドであり、[`parameter_refs`](@ref parameter_refs(vref::InfiniteVariableRef)) が推奨されるユーザ関数として意図されています。
