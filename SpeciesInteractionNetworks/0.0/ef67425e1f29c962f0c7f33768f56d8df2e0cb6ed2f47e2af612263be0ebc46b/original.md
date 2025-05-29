```
speciescontribution(::Type{C}, N::SpeciesInteractionNetwork{<:Partiteness{T}, <:Binary}, sp::T, f, args...; replicates=999, kwargs...) where {C <: PermutationConstraint, T}
```

Returns the contribution of species `sp` to the value of `f(N, args...; kwargs...)`, after [Saavedra2011Strong](@citet). Specifically, this function will generate a species-specific [`nullmodel`](@ref), and then update *in-place* a copy of the network where interactions of species `sp` are randomly re-drawn according to the probabilities under the null model.

Note that for the sake of generality, the function `f` can accept both positional and keyword arguments.

The contribution of a species to the score is defined as

$\frac{f(N)-\mu_f}{\sigma_f}$

where μ and σ are respectively the average and standard deviation of the values of the measure `f` on the randomized networks.

In order to ensure that the networks generated under the null model are informative, we constrain the number of interactions of `sp` in the randomized network to be equal to the number of interactions of `sp` in the original network.

###### References

[Saavedra2011Strong](@citet*)
