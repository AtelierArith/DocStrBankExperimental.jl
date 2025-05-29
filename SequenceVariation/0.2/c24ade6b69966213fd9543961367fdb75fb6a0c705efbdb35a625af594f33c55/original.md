```
refbases(v::Variation)
```

Get the reference bases of `v`. Note that for deletions, `refbases` also returns the base *before* the deletion in accordance with the `REF` field of the [VCF v4 specification](https://samtools.github.io/hts-specs/VCFv4.3.pdf).
