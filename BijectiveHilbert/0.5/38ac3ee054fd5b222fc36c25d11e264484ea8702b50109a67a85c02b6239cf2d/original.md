Simple2D(::Type{T})

The type is a data type to hold the Hilbert index. It should have enough bits to hold all bits of integer axes to encode.

The variant algorithm used differs from the usual Hilbert code because it doesn't need to know the size of the whole grid before computing the code. It looks like a slightly-rotated version of the Hilbert curve, but it has the benefit that it is 1-1 between `(x, y)` and `z`, so you can translate back and forth.

If the size of the axis values or the size of the Hilbert index are too large to be stored in the data types of the axis vector or index, then you'll see an error from a failure of `trunc`, which tries to copy values into the smaller datatype. Solve this by using a larger datatype, so UInt64 instead of UInt32.

It comes from a paper:  N. Chen, N. Wang, B. Shi, A new algorithm for encoding and decoding the Hilbert order. Software—Practice and Experience 2007; 37(8): 897–908.
