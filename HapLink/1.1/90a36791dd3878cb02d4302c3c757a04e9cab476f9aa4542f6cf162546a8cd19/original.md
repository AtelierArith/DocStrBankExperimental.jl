```
vcf(vc::VariationCall, refname::AbstractString) -> VCF.Record
```

Converts `vc` into a `VCF.Record`. `refname` is required and used as the `CHROM` field in the record.
