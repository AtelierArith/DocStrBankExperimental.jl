UInt12Arrays supports the use of 12-bit unsigned integers.

The current design is based on reading 12-bit integers from a vector of byte-multiple unsigned integers (Vector{UInt8}, Vector{UInt16}, Vector{UInt24}).

The default element type is a UInt16 to which provides best usability and performance. However, a UInt12 type is also provided and can be used via a parameter.

Note: The use of UInt16 as the default element may change as the UInt12 type matures and lower level LLVM support emerges.
