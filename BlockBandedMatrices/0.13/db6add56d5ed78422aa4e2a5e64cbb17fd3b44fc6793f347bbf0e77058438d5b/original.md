```
subblockbandwidth(A, i)
```

returns the sub-block lower (`i == 1`) or upper (`i == 2`) bandwidth of `A`, where `A` is a banded-block-banded matrix. In other words, `A[Block(K,J)]` will return a `BandedMatrix` with the returned lower/upper bandwidth.
