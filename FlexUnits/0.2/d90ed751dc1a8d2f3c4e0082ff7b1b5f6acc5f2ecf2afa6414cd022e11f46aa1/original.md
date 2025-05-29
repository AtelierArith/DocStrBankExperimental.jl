```
dimensionalize(f, args::AbstractQuantity...)
```

Converts all arguments to base units, and applies `f` to values and dimensions returns the narrowest possible quanity. Useful for defining  new functions for quantities 

Thus, in order to support `f` for quantities, simply define 

f(dims::AbstractDimensions...) f(args::AbstractQuantity...) = dimensionalize(f, args...)
