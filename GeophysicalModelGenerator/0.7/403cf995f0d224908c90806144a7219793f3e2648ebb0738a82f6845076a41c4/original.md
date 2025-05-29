```
write_ASAGI(fname::String, Data::CartData; 
                    fields::Union{Nothing, Tuple}=nothing, 
                    km_to_m::Bool=false)
```

Writes a CartData structure `Data` to an ASAGI file, which can be read by SeisSol or ExaHype. You can optionally pass a tuple with fields to be written. Note that we can only write individual (scalar) fields to disk, so vector or tensor fields needs to be split first
