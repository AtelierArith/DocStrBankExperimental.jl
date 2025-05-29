```
altbases(v::Variation)
```

Get the alternate bases of `v`. Note that for insertions, `altbases` also returns the base *before* the insertion in accordance with the `ALT` field of the [VCF v4 specification](https://samtools.github.io/hts-specs/VCFv4.3.pdf).
