```
codon_frequency(codon_counts::Matrix{<:Integer}, form::String, dict::CodonDict = DEFAULT_CodonDict)
```

Calculate codon frequency from a matrix of codon counts. Accepts as its first argument a `Matrix{<:Integer}` which is a product of `count_codons()`. `form` can be one of four options: -`net_genomic`: Frequency of each codon across entire genome (matrix). -`net_gene`: Frequency of each codon within each gene (column). -`byAA_genomic`: Frequency of each codon within each amino acid across the entire genome (matrix). -`byAA_gene`: Frequency of each codon within each amino acid within each gene (column). 

If using an alternative genetic code, a custom `CodonDict` can be provided.

# Examples

```jldoctest
julia> codon_counts = count_codons(EXAMPLE_DATA_PATH);

julia> count_matrix = codon_counts[1];

julia> codon_frequency(count_matrix, "net_genomic")[1:5]
5-element Vector{Float64}:
 0.04941242971710299
 0.017114892645228374
 0.021009352696846777
 0.022269444158755328
 0.022257296747490142

julia> codon_frequency(count_matrix, "net_genomic") |> size
(64, 1)

julia> codon_frequency(count_matrix, "net_gene") |> size
(64, 4237)
```
