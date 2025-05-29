```
fwrite(filename::AbstractString, tns::Finch.Tensor)
```

Write the Finch tensor to a file using a file format determined by the file extension. The following file extensions are supported:

  * `.bsp.h5`: [Binsparse](https://github.com/GraphBLAS/binsparse-specification) HDF5 file format
  * `.bspnpy`: [Binsparse](https://github.com/GraphBLAS/binsparse-specification) NumPy and JSON subdirectory format
  * `.mtx`: [MatrixMarket](https://math.nist.gov/MatrixMarket/formats.html#MMformat) `.mtx` text file format
  * `.ttx`: [TensorMarket](https://github.com/willow-ahrens/TensorMarket.jl) `.ttx` text file format
  * `.tns`: [FROSTT](http://frostt.io/tensors/) `.tns` text file format
