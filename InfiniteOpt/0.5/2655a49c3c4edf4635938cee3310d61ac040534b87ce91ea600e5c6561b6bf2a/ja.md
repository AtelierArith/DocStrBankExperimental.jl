```
parameter_refs(dref::DerivativeRef)::Tuple
```

無限微分 `dref` に関連付けられたパラメータ参照を返します。これは、`dref` を定義するために入力されたパラメータ参照を含むタプルとしてフォーマットされています。

**例**

```julia-repl
julia> parameter_refs(deriv)
(t,)
```
