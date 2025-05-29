```
BitString{B,N,T<:Unsigned}
```

Type for storing bitstrings of static size. Holds `B` bits in `N` chunks, where each chunk is of type `T`.

`N` is chosen automatically to accommodate `B` bits as efficiently as possible.

# Constructors

  * `BitString{B,N,T}(::SVector{N,T})`: unsafe constructor. Does not check for ghost bits.
  * `BitString{B,N,T}(i::T)`: as above, but sets `i` as the rightmost chunk.
  * `BitString{B}(::Integer)`: Convert integer to `BitString`. Integer is truncated to the correct number of bits.
