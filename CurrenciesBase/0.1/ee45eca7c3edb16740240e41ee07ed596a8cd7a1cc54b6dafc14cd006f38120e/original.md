```
decimals(m::Monetary) → Int
decimals(s::Symbol)   → Int
decimals(d::DataType) → Int
```

Get the precision, in terms of the number of decimal places after the major currency unit, of the given `Monetary` value or type. Alternatively, if given a symbol, gets the default exponent (the number of decimal places to represent the minor currency unit) for that symbol. Return `-1` if there is no sane minor unit, such as for several kinds of precious metal.
