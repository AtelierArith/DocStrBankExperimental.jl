```
estimate!(buffer::AbstractVector, b::SBit)
estimate!(buffer::AbstractVector, b::VecOrMat{SBit})
estimate(buffer::AbstractVector)
estimate(s::SBitstream)
```

Push `b` into the `buffer` and return the current [`estimate`](#).
