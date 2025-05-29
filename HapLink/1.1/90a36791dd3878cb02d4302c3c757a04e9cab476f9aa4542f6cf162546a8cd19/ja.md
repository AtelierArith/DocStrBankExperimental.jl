```
vcf(vc::VariationCall, refname::AbstractString) -> VCF.Record
```

`vc`を`VCF.Record`に変換します。`refname`は必須で、レコードの`CHROM`フィールドとして使用されます。
