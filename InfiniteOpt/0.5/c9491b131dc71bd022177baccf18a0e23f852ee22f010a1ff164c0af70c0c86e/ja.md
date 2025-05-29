```
raw_parameter_refs(fref::ParameterFunctionRef)::VectorTuple
```

`fref`が依存するパラメータ参照の生の [`VectorTuple`](@ref InfiniteOpt.Collections.VectorTuple) を返します。これは主に内部メソッドであり、[`parameter_refs`](@ref parameter_refs(::ParameterFunctionRef)) が推奨されるユーザ関数として意図されています。
