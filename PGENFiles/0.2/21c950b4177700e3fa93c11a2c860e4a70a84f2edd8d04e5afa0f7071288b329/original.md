```
alt_allele_dosage!(buf, genobuf, p, v; genoldbuf)
```

Computes unphased biallelic dosage of ALT allele. 

  * `buf`: stores dosage values.
  * `genobuf`: stores genotype values.
  * `p`: a `Pgen` object.
  * `v`: a `PgenVariant` object.
  * `genoldbuf`: most recent non-LD-compressed genotypes.

Returns: 

  * `buf`
  * `genobuf`
  * `offset`: end of dosage record on the current variant record track.
