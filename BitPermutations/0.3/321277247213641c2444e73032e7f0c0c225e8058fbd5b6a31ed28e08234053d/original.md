```
AVXCopyGather{T}
```

A permutation backend which uses AVX-512 intrisics to perform a permutation on 16-, 32-, or 64-bit long integers. The input data is copied several times to fill an AVX register, and then a special operation extracts data from it using a mask. Internally, it stores precomputed masks for the forward and backward permutation.
