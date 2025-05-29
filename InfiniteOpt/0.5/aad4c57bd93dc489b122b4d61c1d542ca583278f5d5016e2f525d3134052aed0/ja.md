```
start_value_function(vref::SemiInfiniteVariableRef)::Union{Nothing, Function}
```

特定のサポート値に対して `vref` の開始値を生成するために使用される関数を返します。開始動作が指定されていない場合は `nothing` を返します。

**例**

```julia-repl
julia> start_value_func(vref)
my_func
```
