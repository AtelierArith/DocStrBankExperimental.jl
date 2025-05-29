```
filters(vc::VariationCall) -> Vector{String}
```

`vc`に適用されたすべてのフィルターを取得します。空のFILTERエントリは[VCF spec](https://github.com/samtools/hts-specs#variant-calling-data-files)の下では許可されておらず、空の配列は自動的にすべてのフィルターを`PASS`したと見なされるべきではありません。
