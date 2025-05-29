```
variation(r::VCF.Record, refseq::NucleotideSeq)
```

Construct a `Variation` from `r` applying to `refseq`. There is no validation that `r`'s actually describes a mutation in `refseq`.
