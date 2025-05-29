```julia
transfect(setup, lib, guides, guide_freqs_dist)

```

Simulates the transfection the of the library of guides (`guides`) according to the parameters in [`Crispulator.Library`](@ref) `lib` and the frequencies represented by the Categorical distribution `guide_freqs_dist`.

This function creates a population of cells post-transfection where each cell has single guide RNA present according to the frequencies of the guides in the present in the library. The cells are then grown up so that there are `setup.bottleneck_representation * num_guides` of them. For FACS screens we assume a simple linear expansion of the cells, while for Growth screens the cells grow according as a function of their phenotype and degree of knockdown.
