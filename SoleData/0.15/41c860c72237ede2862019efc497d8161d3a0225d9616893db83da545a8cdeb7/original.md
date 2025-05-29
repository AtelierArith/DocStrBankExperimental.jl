```
minify(dataset::D1)::Tuple{D2,Function} where {D1,D2}
```

Return a *minified* version of a dataset, as well as a backmap for reverting to the original dataset. Dataset minification remaps each scalar values in the dataset to a new value such that the overall order of the values is preserved; the output dataset is smaller in size, since it relies on values of type UInt8, UInt16, UInt32, etc.

See also [`isminifiable`](@ref).
