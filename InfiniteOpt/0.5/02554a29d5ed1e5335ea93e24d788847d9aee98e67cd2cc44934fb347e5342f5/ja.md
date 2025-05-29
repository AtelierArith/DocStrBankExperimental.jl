```
parameter_refs(expr)::Tuple
```

`expr`の無限依存関係を決定するパラメータ参照のタプルを返します。

**例**

```julia-repl
julia> parameter_refs(my_expr)
(t,)
```
