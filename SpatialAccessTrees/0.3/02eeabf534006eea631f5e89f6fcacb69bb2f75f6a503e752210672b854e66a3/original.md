```
permutesat(sat::Sat, π=satpermutation(sat), π′=invperm(π))
```

Permute sat to optimize cache accesses patterns; the database is also copied and permuted. The permuted index is stored in a `PermutedSearchIndex` struct to allow plug and play index interchange.

# Arguments:

  * `sat`: Input `Sat` index.
  * `π`: Permutation.
  * `π′`: Inverse permutation.
