```
AbstractNMRData <: DimensionalData.AbstractDimArray
```

Abstract supertype for objects that wrap an array of NMR data, and metadata about its contents.

`AbstractNMRData`s inherit from [`AbstractDimArray`](https://rafaqz.github.io/DimensionalData.jl/stable/api/#DimensionalData.AbstractDimensionalArray) from DimensionalData.jl. They can be indexed as regular Julia arrays or with DimensionalData.jl [`Dimension`](https://rafaqz.github.io/DimensionalData.jl/stable/api/#DimensionalData.Dimension)s.
