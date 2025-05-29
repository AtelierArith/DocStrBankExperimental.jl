```
PosLenString(buf::Vector{UInt8}, poslen::PosLen, e::UInt8)
```

A custom string representation that takes a byte buffer (`buf`), `poslen`, and `e` escape character, and lazily allows treating a region of the `buf` as a string. Can be used most efficiently as part of a [`PosLenStringVector`](@ref) which only stores an array of `PosLen` (inline) along with a single `buf` and `e` and returns `PosLenString` when indexing individual elements.
