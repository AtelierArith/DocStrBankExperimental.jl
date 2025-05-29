```
upreferred(x::Units)
```

Return units which are preferred for the dimensions of `x`, which may or may not be equal to `x`, as specified by the [`preferunits`](@ref) function. If you are using the factory defaults, this function will return a product of powers of base SI units.
