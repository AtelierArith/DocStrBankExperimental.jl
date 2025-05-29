```
parameter_refs(vref::InfiniteVariableRef)::Tuple
```

無限変数 `vref` に関連付けられたパラメータ参照を返します。これは、`vref` を定義するために入力されたパラメータ参照を含むタプルとしてフォーマットされています。

**例**

```julia-repl
julia> @variable(model, T, Infinite(t))
T(t)

julia> parameter_refs(T)
(t,)
```
