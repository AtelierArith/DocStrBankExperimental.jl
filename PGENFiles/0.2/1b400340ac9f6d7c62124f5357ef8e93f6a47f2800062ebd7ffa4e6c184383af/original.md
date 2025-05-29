```
ref_allele_dosage(p, v)
```

Computes unphased biallelic dosage of REF allele. 

  * `p`: a `Pgen` object.
  * `v`: a `PgenVariant` object.

Returns: 

  * `buf`: stores dosage values.
  * `genobuf`: stores genotype values.
  * `offset`: end of dosage record on the current variant record track.
