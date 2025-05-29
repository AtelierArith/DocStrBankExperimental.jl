```
parameter_refs(fref::ParameterFunctionRef)::Tuple
```

`fref` に関連付けられたパラメータ参照を返します。これは、`fref` を定義するために入力されたパラメータ参照を含むタプルとしてフォーマットされています。

**例**

```julia-repl
julia> parameter_refs(p_func)
(t,)
```
