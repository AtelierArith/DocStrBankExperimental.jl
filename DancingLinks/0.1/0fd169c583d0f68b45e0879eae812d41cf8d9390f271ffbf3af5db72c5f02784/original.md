```
    convert_nanoseconds(nanosecs::UInt64; # from time_ns() function
                    [ncols]::Integer = 0, # < 0 = discard leading zero values; print most significant column first (cf examples below)
                    [units]::Union{Nothing, Symbol}=nothing,  # != nothing : eg. :ms; last columns is in these units
                                                            # otherwise last column is arbitrary units
                                                            # units = :d, :h, :m, {:s|:sec}, :ms, {:mus|μs}, :ns
                    [omitunits]::Bool=false # whether or not to print the units string
                    )::String
```

This function is to be used in conjunction with, for eg, `time_ns()`

# Examples

```
t = 1.500600e9 # nanoseconds
convert_nanoseconds(t, ncols = 0, units=nothing)   -> "01:500:600μs"
convert_nanoseconds(t, ncols = +1, units=nothing)  -> "1500600μs"
convert_nanoseconds(t, ncols = -1, units=nothing)  -> "2s"
convert_nanoseconds(t, ncols = +2, units=nothing)  -> "1500:600μs"
convert_nanoseconds(t, ncols = -2, units=nothing)  -> "01:501ms"
convert_nanoseconds(t, ncols = +3, units=:ms)      -> "00:01:501ms"
convert_nanoseconds(t, ncols = -3, units=:ms)      -> "01:501ms"
```
