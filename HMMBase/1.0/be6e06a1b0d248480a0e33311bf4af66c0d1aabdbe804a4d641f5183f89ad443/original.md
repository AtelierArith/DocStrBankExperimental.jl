```
remapseq(seq, ref) -> Vector{Integer}
```

Find the permutations of `seq` indices that maximize the overlap with `ref`.

**Arguments**

  * `seq::Vector{Integer}`: sequence to be remapped.
  * `ref::Vector{Integer}`: reference sequence.

**Example**

```julia
ref = [1,1,2,2,3,3]
seq = [2,2,3,3,1,1]
remapseq(seq, ref)
# [1,1,2,2,3,3]
```
