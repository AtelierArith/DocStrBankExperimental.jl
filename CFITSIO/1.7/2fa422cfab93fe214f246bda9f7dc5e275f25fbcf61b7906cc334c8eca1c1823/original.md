```
fits_create_binary_tbl(f::FITSFile, numrows::Integer,
                       coldefs::Union{Array{NTuple{3,String}}, Array{NTuple{2,String}}},
                       extname::Union{String, Nothing} = nothing)
```

Append a new HDU containing a binary table. The meaning of the parameters is the same as in a call to [`fits_create_ascii_tbl`](@ref).

In general, one should pick this function for creating tables in a new HDU, as binary tables require less space on the disk and are more efficient to read and write. (Moreover, a few datatypes are not supported in ASCII tables).
