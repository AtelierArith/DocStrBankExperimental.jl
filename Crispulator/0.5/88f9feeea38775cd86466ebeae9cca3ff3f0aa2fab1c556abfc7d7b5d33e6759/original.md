Wrapper containing all library construction parameters

  * `knockdown_dist`: Distribution of guide knockdown efficiencies
  * `knockdown_probs`
  * `max_phenotype_dists`: Maximum phenotype categories mapped to their probability of being selected and the distribution to draw from if they are selected.

    ## Example

    The basic layout is a `Dict` mapping a class name to a tuple of the probability of selecting this class and then the [`Distributions.Sampleable`](https://juliastats.github.io/Distributions.jl/latest/types.html#Sampleable-1) from which to draw a random phenotype from this class. The probabilities across all the classes should add up to 1.

    ```julia
    max_phenotype_dists = Dict{Symbol, Tuple{Float64, Sampleable}}(
        :inactive => (0.60, Delta(0.0)),
        :negcontrol => (0.1, Delta(0.0)),
        :increasing => (0.3, truncated(Normal(0.1, 0.1), 0.025, 1)),
    );
    Library(max_phenotype_dists, CRISPRi());
    ```

    For example, here we are making three different classes of "genes": the first group are :inactive, i.e. they have no phenotype, so we'll set their phenotypes to 0.0 using a [`Crispulator.Delta`](@ref). We'll also make them 60% of all the genes. The second group are the negative controls :negcontrol (the only required group) which make up 10% of the population of genes and also have no effect. The final group is :increasing which makes up 30% of all genes and which are represented by a Normal(μ=0.1, σ=0.1) distribution clamped between 0.025 and 1.

  * `phenotype_probs`
  * `kd_phenotype_relationships`: Knockdown-phenotype relationships mapped to their probability of being selected and their respective [`Crispulator.KDPhenotypeRelationship`](@ref)

  * `relationship_probs`
  * `cas9_behavior`: Whether this library is [`Crispulator.CRISPRi`](@ref) or [`Crispulator.CRISPRn`](@ref)
