```
qec_read(io::IO) -> Vector{Dict{Symbol,Any}}
qec_read(filename::AbstractString) -> Vector{Dict{Symbol,Any}}
```

Read simulation run data from the given I/O stream or file.

Run data is expected in the format written by [`qec_write`](@ref) (i.e. a JSON array of objects using default JSON encoding of the format specified by [`qec_run`](@ref)). The read data is converted to the specified return type as follows: dictionary keys are converted to symbols, `:n_k_d` entries are converted to tuples, and vector types are inferred from their elements. If this conversion fails, an exception is thrown.

The JSON format is compatible with the format used by the Python package [qecsim](https://github.com/qecsim/qecsim).

See also [`qec_write`](@ref).
