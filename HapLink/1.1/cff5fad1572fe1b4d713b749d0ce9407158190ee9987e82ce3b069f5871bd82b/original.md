```
occurrence_matrix(
    haplotype::AbstractArray{Variation{S,T}},
    reads::AbstractArray{Haplotype{S,T}},
) where {S<:BioSequence,T<:BioSymbol}
occurrence_matrix(
    haplotype::Haplotype{S,T},
    reads::AbstractArray{S,T}
) where {S<:BioSequence,T<:BioSymbol}
```

Determine how many times the variants in `haplotype` appear in `reads` as an $N$- dimensional matrix.

# Arguments

  * `haplotype::AbstractArray{Variation}`: A `Vector` of `Variation`s or a `Haplotype` to search   for as a haplotype
  * `reads::AbstractArray{Haplotype}`: The reads to search for `haplotype` in

# Returns

  * `2x2x... Array{Int, length(haplotype)}`: An $N$-dimensional matrix where $N$ is   the number of variant positions in `readmatches`. The $1$ index position in the   $n$th dimension represents the number of times the $n$th variant position was found   to have the reference base called, while the $2$ index position represents the number   of times the $n$th variant position was found to have the alternate base called. E.g.   `first(occurrence_matrix(reads))` gives the number of times the all-reference base   haplotype was found in `reads`, while `occurrence_matrix(reads)[end]` gives the number   of times the all-alternate base haplotype was found.
