```
prop(io, propertyname[, proptype=Any])
```

Get a trace property from `io::JSeis` where `propertyname` is either `String` or `TracePropertyDef`. Note that if  `propertyname` is a String, then this method produces a type-unstable result. For example:

```julia
io = jsopen("data.js")
p = prop(io, "REC_X")            # using a `String`, output type of prop is not inferred
p = prop(io, "REC_X", Float32)   # using a `String`, output type of prop is inferred using `Float32`
p = prop(io, stockprop[:REC_X])  # using a `TracePropertyDef`, output type of prop is inferred
```

Note that in the examples above, the string "REC*X" can be replaced by the symbol `REC*X`.
