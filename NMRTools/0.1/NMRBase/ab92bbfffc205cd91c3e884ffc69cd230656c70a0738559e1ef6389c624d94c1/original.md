```
NMRData <: AbstractNMRData
NMRData(A::AbstractArray{T,N}, dims; kw...)
NMRData(A::AbstractNMRData; kw...)
```

A generic [`AbstractNMRData`](@ref) for NMR array data. It holds memory-backed arrays.

# Keywords

  * `dims`: `Tuple` of `NMRDimension`s for the array.
  * `name`: `Symbol` name for the array, which will also retreive named layers if `NMRData`   is used on a multi-layered file like a NetCDF.
  * `missingval`: value representing missing data, normally detected from the file. Set manually   when you know the value is not specified or is incorrect. This will *not* change any   values in the NMRData, it simply assigns which value is treated as missing.

# Internal Keywords

In some cases it is possible to set these keywords as well.

  * `data`: can replace the data in an `AbstractNMRData`
  * `refdims`: `Tuple of` position `Dimension`s the array was sliced from, defaulting to `()`.
