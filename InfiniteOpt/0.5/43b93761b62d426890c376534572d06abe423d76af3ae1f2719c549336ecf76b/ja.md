```
JuMP.set_binary(vref::UserDecisionVariableRef)::Nothing
```

`JuMP.set_binary`を拡張して、`InfiniteOpt`変数をバイナリ変数として指定します。`vref`が整数変数の場合はエラーになります。

**例**

```julia-repl
julia> set_binary(vref)

julia> is_binary(vref)
true
```
