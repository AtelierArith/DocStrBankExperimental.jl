```
measure_function(mref::MeasureRef)::JuMP.AbstractJuMPScalar
```

`mref`に関連付けられた関数を返します。

**例**

```julia-repl
julia> measure_function(meas)
y(x, t) + 2
```
