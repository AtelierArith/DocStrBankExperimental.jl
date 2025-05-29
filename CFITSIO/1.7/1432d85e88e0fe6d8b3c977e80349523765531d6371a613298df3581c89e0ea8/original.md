```
fits_create_ascii_tbl(f::FITSFile, numrows::Integer,
                      coldefs::Union{Array{NTuple{3,String}}, Array{NTuple{2,String}}},
                      extname::Union{String, Nothing} = nothing)
```

Append a new HDU containing an ASCII table.

The table will have `numrows` rows (this parameter can be set to zero), each initialized with the default value. In order to create a table, the programmer must specify the characteristics of each column. The columns are specified by the `coldefs` variable, which is an array of tuples. Each tuple must have two or three string fields:

1. The name of the column.
2. The data type and the repetition count. It must be a string made by a number (the repetition count) followed by a letter specifying the type (in the example above, `D` stands for `Float64`, `E` stands for `Float32`, `A` stands for `Char`). Refer to the CFITSIO documentation for more information about the syntax of this parameter.
3. The unit of this field. This is used to set the corresponding `TUNITn` keywords. If `coldefs` is a two-tuple, the unit keywords are left unset. If the third field of a tuple is an empty string, the corresponding unit keyword is also left unset.

The value of `extname` sets the "extended name" of the table, i.e., a string that in some situations can be used to refer to the HDU itself. This may be omitted by setting `extname` to `nothing` (which is the default behavior).

Note that, unlike for binary tables, CFITSIO puts some limitations to the types that can be used in an ASCII table column. Refer to the CFITSIO manual for further information.

See also [`fits_create_binary_tbl`](@ref) for a similar function which creates binary tables. In general, one should pick this function for creating tables in a new HDU, as binary tables require less space on the disk and are more efficient to read and write. (Moreover, a few datatypes are not supported in ASCII tables).
