```
filters(vc::VariationCall) -> Vector{String}
```

Gets all filters that have been applied to `vc`. Note that an empty FILTER entry is not permitted under the [VCF spec](https://github.com/samtools/hts-specs#variant-calling-data-files), and an empty array should not automatically be considered to have `PASS`ed all filters.
