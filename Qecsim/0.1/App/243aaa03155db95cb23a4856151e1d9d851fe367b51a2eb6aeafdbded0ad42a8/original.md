```
qec_write(io::IO, data...)
qec_write(filename::AbstractString, data...)
```

Write simulation run data to the given I/O stream or file.

Run data is expected in the format specified by [`qec_run`](@ref) and written as a JSON array of objects using default JSON encoding. No checking of the format of the given data is performed. The file version of this method will refuse to overwrite an existing file, instead attempting to log the unwritten data and throwing an exception.

The JSON format is compatible with the format used by the Python package [qecsim](https://github.com/qecsim/qecsim).

See also [`qec_read`](@ref).
