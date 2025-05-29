```julia
DAM(; kwargs...) -> AdaptiveResonance.SFAM

```

# Summary

Constructs a Default ARTMAP module using a SFAM module using Default ARTMAP's choice-by-difference activation function.

Default ARTMAP is a variant of SFAM, using the [`AdaptiveResonance.opts_SFAM`](@ref) options. This constructor sets the activation to `:choice_by_difference` in addition to the keyword argument options you provide.

# Arguments

  * `kwargs`: keyword arguments of Simplified FuzzyARTMAP options (see [`AdaptiveResonance.opts_SFAM`](@ref))

# References:

1. G. P. Amis and G. A. Carpenter, 'Default ARTMAP 2,' IEEE Int. Conf. Neural Networks - Conf. Proc., vol. 2, no. September 2007, pp. 777-782, Mar. 2007, doi: 10.1109/IJCNN.2007.4371056.

# Method List / Definition Locations

```julia
DAM(; kwargs...)
```

defined at [`packages/AdaptiveResonance/wgSPV/src/ARTMAP/variants.jl:29`](file:///home/terasaki/.julia/packages/AdaptiveResonance/wgSPV/src/ARTMAP/variants.jl).
