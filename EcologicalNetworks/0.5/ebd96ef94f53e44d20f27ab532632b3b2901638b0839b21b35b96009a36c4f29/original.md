```
EAJS(N::T; dims::Union{Nothing,Integer}=nothing) where {T <: UnipartiteNetwork}
```

Extended Additive Jaccard Similarity for pairs of species in the network. AJS varies between 0 (no common species) to 1 (same profiles). This function can be used to measure AJS based on only successors or predecessors, using the `dims` argument.

Note that this function counts all interactions up to a distance of 50 to define the neighbourhood of a species. This should be more than sufficient for most ecological networks.

#### References

Gao, P., Kupfer, J.A., 2015. Uncovering food web structure using a novel trophic similarity measure. Ecological Informatics 30, 110–118. https://doi.org/10.1016/j.ecoinf.2015.09.013
