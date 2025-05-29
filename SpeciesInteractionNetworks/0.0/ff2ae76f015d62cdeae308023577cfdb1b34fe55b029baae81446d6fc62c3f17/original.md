```
linearfilter(N::SpeciesInteractionNetwork{<:Partiteness, <:Binary}; α::Vector{T}=ones(4)) where {T <: AbstractFloat}
```

The linear filter returns a probability of observing an interaction as a function of a linear combination of the observed value of the interaction, the generality and vulnerability of the species, and the connectance of the network. It is also used to provide a generic implementation of [`nullmodel`](@ref).

Specifically, the probability of an interaction is expressed as a weighted average, the weights being given as the vector `α`.

The vector `α` has four elements, all positive, and $\sum \alpha = 1$ (this is enforced internally, and does not need to be checked by the user).

$\alpha_1$ is the weight of the original interaction; it helps to think of it as a penalization parameter, that explains how important the original observation is.

$\alpha_2$ is the weight of generality; it regulates how important the probability of the species *establishing* an interaction is in the resulting network.

$\alpha_3$ is the weight of vulnerability; it regulates how important the probability of the species *receing* an interaction is in the resulting network.

$\alpha_4$ is the weight of connectance.

###### References

[Stock2017Linear](@citet*)
