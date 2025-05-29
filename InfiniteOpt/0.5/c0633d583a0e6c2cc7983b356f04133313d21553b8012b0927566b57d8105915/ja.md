```
JuMP.set_integer(vref::UserDecisionVariableRef)::Nothing
```

`JuMP.set_integer`を拡張して、`InfiniteOpt`変数を整数変数として指定します。`vref`がバイナリ変数の場合はエラーになります。

**例**

```julia-repl
julia> set_integer(vref)

julia> is_integer(vref)
true
```
