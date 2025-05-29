```
time_slice(m; temporal_block=anything, t=anything)
```

An `Array` of `TimeSlice`s in model `m`.

# Arguments

  * `temporal_block::Union{Object,Vector{Object}}`: only return `TimeSlice`s in these blocks.
  * `t::Union{TimeSlice,Vector{TimeSlice}}`: only return `TimeSlice`s that are also in this collection.
