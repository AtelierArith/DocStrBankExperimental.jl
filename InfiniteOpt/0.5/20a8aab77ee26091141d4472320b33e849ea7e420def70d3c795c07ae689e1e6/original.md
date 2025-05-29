```
measure_function(mref::MeasureRef)::JuMP.AbstractJuMPScalar
```

Return the function associated with `mref`.

**Example**

```julia-repl
julia> measure_function(meas)
y(x, t) + 2
```
