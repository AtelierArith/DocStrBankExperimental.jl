```
SymmetricTensor(frame, bls, bln, dats, sqr)
```

Construct a symmetric tensor.

# Arguments

  * `frame::ArrayNArrays{T,N}`: the raw data.
  * `bls::Int`: the size of ordinary block (the same in each direction).
  * `bln::Int`: maximal number of blocks in each direction.
  * `dats::Int`: the size of data stored (the same in each direction).
  * `sqr::Bool`: if all blocks are squares (N-squares).
