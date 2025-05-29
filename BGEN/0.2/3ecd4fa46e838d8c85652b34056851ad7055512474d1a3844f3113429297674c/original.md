```
minor_allele_dosage!(b::Bgen, v::BgenVariant; T=Float32,
mean_impute=false, clear_decompressed=false)
```

Given a `Bgen` struct and a `BgenVariant`, compute minor allele dosage. The result is stored inside `v.genotypes.dose`, which can be cleared using `clear!(v)`.

  * `T`: type for the results
  * `mean_impute`: impute missing values with the mean of nonmissing values
  * `clear_decompressed`: clears decompressed byte string after execution if set `true`
