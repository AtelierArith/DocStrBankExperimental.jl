```julia
to_hdf5(ptdf, filename; compress, compression_level, force)

```

Serialize the PTDF to an HDF5 file.

# Arguments

  * `ptdf::PTDF`: matrix
  * `filename::AbstractString`: File to create
  * `compress::Bool`: Whether to enabled compression, defaults to true.
  * `compression_level::Int`: Compression level to use if compression is enabled.
  * `force::Bool`: Whether to overwrite the file if it already exists, defaults to false.
