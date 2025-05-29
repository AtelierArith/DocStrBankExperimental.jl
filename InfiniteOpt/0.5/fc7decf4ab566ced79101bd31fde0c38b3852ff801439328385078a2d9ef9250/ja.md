```
parameter_values(vref::PointVariableRef)::Tuple
```

ポイント変数 `vref` に関連付けられたサポートポイントを返します。

**例**

```julia-repl
julia> @variable(model, T, Infinite(t))
T(t)

julia> @variable(model, T0, Point(T, 0))
T0

julia> parameter_values(T0)
(0,)
```
