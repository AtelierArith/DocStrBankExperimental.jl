```
uconvert(utrans::AffineTransform, x)
```

Apply the unit conversion formula "utrans" to value "x", can be used to apply unit conversions on unitless values

julia> uconvert(u"m/s"|>u"km/hr", 1.0) 3.5999999999999996
