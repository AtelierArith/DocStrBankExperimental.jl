```
similar_library(lib::Library, d::FullDim, T::Type)
```

Returns a library that supports polyhedra of full dimension `T` with coefficient type `T`. If `lib` does not support it, this commonly calls `default_library(d, T)`.
