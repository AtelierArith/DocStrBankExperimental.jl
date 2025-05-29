```
outValCopy(pb::ParamBox{T, V}) where {T} -> ParamBox{T, V, typeof(Quiqbox.itself)}
```

Return a new `ParamBox` of which the input variable's value is equal to the output  variable's value of `pb`.
