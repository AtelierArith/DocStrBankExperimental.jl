Static indexable bit vector.

`SucVector` requires 5/4 bits per bit in order to keep bits and the number of bits (i.e. a `SucVector` object becomes ~25% bigger when converted from a `BitVector` object). Bits are split into blocks: four chunks of 64 bits are stored in a block and blocks are stored in a vector. Blocks are contiguous in momery so that memory cache works efficiently.

The number of bits is limited up to 2^40 bits. This is 128GiB so would be enough in most cases.

Let `n` be the length of a `SucVector`, the asymptotic query times are

  * getindex: `O(1)`
  * rank: `O(1)`
  * select: `O(log n)`
