```julia
struct CosineRing{N, M, T} <: VLBISkyModels.AbstractImageTemplate
```

A flexible symmetric ring model. The thickness is modeled as a cosine expansion with `N` terms and the slash by a expansion with `M` terms.

# Details

The ring is forced to be symmetric for a significant speed boost over CosineRing. The thickness of the ring is modeled by a cosine expansion in azimuthal angle. `N` specifies the number of cosine modes to fit, where the first mode is the constant thickness portion and so has no corresponding angle. The slash is modeled as a separate cosine expansion, with `M` terms. Here the zero order term is forced to be unity, so `M` defines the `M` additional terms.
