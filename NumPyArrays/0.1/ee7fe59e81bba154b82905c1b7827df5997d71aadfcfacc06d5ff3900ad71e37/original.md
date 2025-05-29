```
NumPyArray{T,N}(po::PyObject)
```

NumPyArray is a wrapper around a PyCall.PyArray. It is an AbstractArray. The main purpose of a NumPyArray is so to provide a constructor to generalize the conversion of Julia arrays into NumPyArrays. `T` is the element type of the array. `N` is the number of dimensions.

For other uses, such as wrapping an existing array from NumPy, use `PyCall.PyArray`.

Use `PyObject` and `PyArray` methods to convert `NumPyArray` into those types.
