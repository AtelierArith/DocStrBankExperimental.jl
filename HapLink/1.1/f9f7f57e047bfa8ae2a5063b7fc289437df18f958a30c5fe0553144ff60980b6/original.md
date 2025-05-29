```
function ishaplotype(
    haplotype::Union{AbstractArray{Variation{S,T}}, Haplotype{S,T}},
    reads::AbstractArray{Haplotype{S,T}};
    frequency::Union{Float64,Nothing}=nothing,
    significance::Union{Float64,Nothing}=nothing,
    depth::Union{Int,Nothing}=nothing,
) where {S<:BioSequence,T<:BioSymbol}
```

Determines if a call of `haplotype` is supported by the sequences in `reads` based upon the provided keyword criteria.

# Arguments

  * `haplotype::Union{AbstractArray{Variation}, Haplotype}`: A `Vector` of `Variation`s or a   `Haplotype` to search for as a haplotype
  * `reads::AbstractArray{Haplotype}`: The reads to search for `haplotype` in

# Keywords

  * `frequency::Union{Float64,Nothing}=nothing`: The minimum number of times the entire   `haplotype` must appear within `reads` compared to the number of reads to return `true`
  * `significance::Union{Float64,Nothing}=nothing`: The $χ^2$ significance level ($α$)   of linkage disequilibrium that a haplotype must surpass to return `true`
  * `depth::Union{Int,Nothing}=nothing`: The minimum number of times the entire `haplotype`   must appear within `reads` to return `true`

# Extended help

Linkage disequilibrium ($Δ$) is calculated by

$$
Δ = P_{reference} - \prod_i P_{ref,i}
$$

where

  * $P_{reference}$ is the probability of finding a read that contains only reference   (consensus) bases
  * $P_{ref,i}$ is the probability of finding a read that contains the reference (consensus)   base for variant $i$ within a haplotype

and the $χ^2$ statistic is calculated by

$$
χ^2 = \frac{
            Δ^2 n
        }
        {
            \left(\prod_i^N {P_{ref,i} \left(1 - P_{ref,i}\right)}\right)^\frac{2}{N}
        }
$$

where

  * $N$ is the number of `Variation`s in `haplotype` (i.e., `length(haplotype)`)
  * $n$ is the number of total reads sampled (i.e. `length(reads)`)

The significance is then calculated from the cumulative $χ^2$ distribution function.
