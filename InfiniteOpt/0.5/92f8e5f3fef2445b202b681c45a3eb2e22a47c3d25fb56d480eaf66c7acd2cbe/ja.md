```
raw_parameter_refs(vref::InfiniteVariableRef)::VectorTuple
```

`vref` が依存するパラメータ参照の生の [`VectorTuple`](@ref InfiniteOpt.Collections.VectorTuple) を返します。これは主に内部メソッドであり、[`parameter_refs`](@ref parameter_refs(vref::InfiniteVariableRef)) が推奨されるユーザ関数として意図されています。
