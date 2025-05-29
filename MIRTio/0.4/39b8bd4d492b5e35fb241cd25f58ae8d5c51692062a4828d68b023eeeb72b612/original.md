```
esc = h5_get_ESC(filename::String; T::Type = ComplexF32)
```

Return `Array` of ESC (emulated single coil) data from file.

HDF5.jl reads the data differently than Python's h5py. This is significant because the fastMRI paper says that the datasets have certain dimensionality, but the dimensions are permuted in Julia compared to Python, hence the calls to `permutedims` in the following functions.
