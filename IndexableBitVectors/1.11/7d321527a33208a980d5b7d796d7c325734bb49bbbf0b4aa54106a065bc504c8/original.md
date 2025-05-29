Compressed indexable bit vector.

`RRR` compresses a bit vector in an information-theoretically optimal representation. This compression is based on local abundance of bits; if 0s or 1s are clustered in a bit vector, it will be compressed even when the numbers of 0s and 1s are globally equal.

Let `n` be the length of a `RRR`, the asymptotic query times are

  * getindex: `O(1)`
  * rank: `O(1)`
  * select: `O(log n)`

See (Raman et al, 2007, doi:10.1145/1290672.1290680) for more details.
