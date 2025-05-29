```
fit(HDMR,@model(h ~ x1 + x2, c ~ x1),df,counts; <keyword arguments>)
```

Fits a HDMR but takes a model formula and dataframe instead of the covars matrix. See also [`fit(::HDMR)`](@ref).

`h` and `c` on the lhs indicate the model for zeros and positives, respectively.
