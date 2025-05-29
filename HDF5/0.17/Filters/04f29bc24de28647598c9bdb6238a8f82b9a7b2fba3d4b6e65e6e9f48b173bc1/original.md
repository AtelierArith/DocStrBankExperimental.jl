HDF5.Filters

This module contains the interface for using filters in HDF5.jl.

# Example Usage

```julia
using HDF5
using HDF5.Filters

# Create a new file
fn = tempname()

# Create test data
data = rand(1000, 1000)

# Open temp file for writing
f = h5open(fn, "w") 

# Create datasets
dsdeflate = create_dataset(f, "deflate", datatype(data), dataspace(data),
                           chunk=(100, 100), deflate=3)

dsshufdef = create_dataset(f, "shufdef", datatype(data), dataspace(data),
                           chunk=(100, 100), shuffle=true, deflate=3)

dsfiltdef = create_dataset(f, "filtdef", datatype(data), dataspace(data),
                           chunk=(100, 100), filters=Filters.Deflate(3))

dsfiltshufdef = create_dataset(f, "filtshufdef", datatype(data), dataspace(data),
                               chunk=(100, 100), filters=[Filters.Shuffle(), Filters.Deflate(3)])

# Write data
write(dsdeflate, data)
write(dsshufdef, data)
write(dsfiltdef, data)
write(dsfiltshufdef, data)

close(f)
```

## Additonal Examples

See [test/filter.jl](https://github.com/JuliaIO/HDF5.jl/blob/master/test/filter.jl) for further examples.
