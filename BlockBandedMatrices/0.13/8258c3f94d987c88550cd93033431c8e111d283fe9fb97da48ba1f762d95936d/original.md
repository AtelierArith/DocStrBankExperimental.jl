```
subblockbandwidths(A)
```

returns the sub-block bandwidths of `A`, where `A` is a banded-block-banded matrix. In other words, `A[Block(K,J)]` will return a `BandedMatrix` with bandwidths given by `subblockbandwidths(A)`.
