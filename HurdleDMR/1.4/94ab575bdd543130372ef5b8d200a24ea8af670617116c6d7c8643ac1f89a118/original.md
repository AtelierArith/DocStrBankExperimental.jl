```
fit(DMR,@model(c ~ x1*x2),df,counts; <keyword arguments>)
```

Fits a DMR but takes a model formula and dataframe instead of the covars matrix. See also [`fit(::DMR)`](@ref).

`c` must be specified on the lhs to indicate the model for counts.
