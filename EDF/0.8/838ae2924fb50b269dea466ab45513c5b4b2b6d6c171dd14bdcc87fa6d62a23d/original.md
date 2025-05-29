```
EDF.File{T,I<:IO}
```

Type representing an EDF file with samples encoded as values of type `T`, which is `Int16` for EDF files and `Int24` (internally defined) for BDF files.

# Fields

  * `io::I`
  * `header::FileHeader`
  * `signals::Vector{Union{Signal{T},AnnotationsSignal}}`
