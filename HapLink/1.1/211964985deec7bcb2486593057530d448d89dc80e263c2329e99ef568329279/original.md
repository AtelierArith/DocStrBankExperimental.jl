```
VariationCall
```

Represents a `Variation` that is supported by aligned reads with sufficient metadata to support or refute its validity. It is designed to be converted into a line in [Variant Call Format](https://github.com/samtools/hts-specs#variant-calling-data-files), or a [`VCF.Record`](https://rasmushenningsson.github.io/VariantCallFormat.jl/stable/vcf-bcf/).

# Fields

  * `variation::Variation`: The `Variation` of this call
  * `quality::Union{Nothing,Number}`: Phred quality of the basecall for `variation`
  * `filter::Vector{String}`: Indicator if `variation` has passed filters and is actually a variant call, or a list of criteria that have failed it
  * `depth::Union{Nothing,UInt}`: The number of reads that cover `leftposition(variation)`
  * `strandbias::Union{Nothing,Float64}`: The fraction of times `variation` appears on a positive strand
  * `altdepth::Union{Nothing,UInt}`: The number of types `variation` occurs
  * `readpos::Union{Nothing,UInt}`: The averagerelative position of `variation` in each read
  * `pvalue::Union{Nothing,Float64}`: The Fisher's Exact Test $p$-value of this call
