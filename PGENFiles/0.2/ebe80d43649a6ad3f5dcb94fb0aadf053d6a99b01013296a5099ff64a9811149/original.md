```
get_genotypes!(buf, p, v; ldbuf)
```

Computes unphased biallelic dosage of ALT allele. 

  * `buf`: stores genotype values.
  * `p`: a `Pgen` object.
  * `v`: a `PgenVariant` object.
  * `ldbuf`: most recent non-LD-compressed genotypes.

Returns: 

  * `buf`: resulting genotype values
  * `variant_record`: current record for variant
  * `offset`: end of dosage record on the current variant record track.
