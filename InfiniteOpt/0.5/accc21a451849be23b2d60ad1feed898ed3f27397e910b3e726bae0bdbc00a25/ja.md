```
infinite_variable_ref(vref::PointVariableRef)::GeneralVariableRef
```

点変数 `vref` に関連付けられた `InfiniteVariableRef` を返します。

**例**

```julia-repl
julia> @variable(model, T, Infinite(t))
T(t)

julia> @variable(model, T0, Point(T, 0))
T0

julia> infinite_variable_ref(T0)
T(t)
```
