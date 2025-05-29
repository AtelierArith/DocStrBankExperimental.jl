`function AMT(x::Number)`

Generates the default `AMOUNTS` from `a`, based on its unit dimensions.  The eltype-undecorated `Quantity` constructors are evoked, so that the resulting type precision is taken from the `x` argument. This function is extensively used in operations that result in a unit change.
