```
get_genotypes(p, v)
```

Computes unphased biallelic dosage of ALT allele. 

  * `p`: a `Pgen` object.
  * `v`: a `PgenVariant` object.

Returns: 

  * `buf`: resulting genotype values
  * `variant_record`: current record for variant
  * `offset`: end of dosage record on the current variant record track.
