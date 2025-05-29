```
UInt12Array{T, B, N}(data::B [, size::NTuple{N,Int} ])
UInt12Array{T, B, N}(undef    , size::NTuple{N,Int}  )
```

UInt12Array represents an array of densely packed 12-bit integers.

UInt12AArray has the following parameters: `T` - Element type of the UInt12Array. Typically this might be either UInt12 or     UInt16. Default is UInt12Arrays.default_eltype. `B` - Base type for the UInt12Array's internal vector storage. `N` - Number of dimensions of the array.
