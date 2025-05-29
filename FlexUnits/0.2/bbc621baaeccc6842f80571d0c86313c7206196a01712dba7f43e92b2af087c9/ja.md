```
uconvert(utrans::AffineTransform, x)
```

単位変換式「utrans」を値「x」に適用します。単位のない値に単位変換を適用するために使用できます。

julia> uconvert(u"m/s"|>u"km/hr", 1.0) 3.5999999999999996
