```
probabilities!(b::Bgen, v::BgenVariant; T=Float32, clear_decompressed=false)
```

Given a `Bgen` struct and a `BgenVariant`, compute probabilities. The result is stored inside `v.genotypes.probs`, which can be cleared using `clear!(v)`.

  * T: type for the resutls
  * `clear_decompressed`: clears decompressed byte string after execution if set `true`
