```
variationinfos(
    query::Union{SAM.Record,BAM.Record}, reference::NucleotideSeq
) -> Vector{VariationInfo}
variationinfos(
    query::Union{AbstractString,AbstractPath},
    reference::Union{AbstractString,AbstractPath}
) -> Vector{VariationInfo}
```

`query`に対する`reference`のアライメントに基づいて`Variation`を呼び出し、`query`内で見つかったすべての変異呼び出しを`Vector{VariationInfo}`として返します。
