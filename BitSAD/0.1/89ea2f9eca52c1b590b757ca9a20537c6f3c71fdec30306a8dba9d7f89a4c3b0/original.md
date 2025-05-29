```
generate(s::SBitstream, T::Integer = 1)
generate!(s::SBitstream, T::Integer = 1)
```

Generate `T` samples of the bitstream, `s`. Add them to the queue for `generate!`, otherwise return the vector of bits.
