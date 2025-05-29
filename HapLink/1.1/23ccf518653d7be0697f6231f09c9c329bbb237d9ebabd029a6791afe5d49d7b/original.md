```
call_variant(
    pileup::VariationPileup,
    α::Float64;
    D::Union{Nothing,Int}=nothing,
    Q::Union{Nothing,Float64}=nothing,
    X::Union{Nothing,Float64}=nothing,
    F::Union{Nothing,Float64}=nothing,
    S::Union{Nothing,Float64}=nothing,
) -> VariationCall
```

Calls variant from a `pileup`.

# Arguments

  * `pileup::VariationPileup`: The pileup to call variants from
  * `α::Float64`: Fisher's Exact Test significance ($α$) level to call variants

# Keywords

!!! note
    Leave any keyword undefined to skip filtering based on that field


  * `D::Union{Nothing,Int}=nothing`: Minimum total read depth for a variant to be called
  * `Q::Union{Nothing,Float64}=nothing`: Minimum average Phred quality for a variant to be   called
  * `X::Union{Nothing,Float64}=nothing`: Maximum average distance variant can be from read   edge to be called
  * `F::Union{Nothing,Float64}=nothing`: Minimum alternate frequency for a variant to be   called
  * `S::Union{Nothing,Float64}=nothing`: Maximum proportion of the number of times variant can   appear on one strand versus the other
