```
SANDI(
    soma::Sphere,
    neurite::Stick,
    extra::Iso,
    fracs::Vector{Float64}
    )
```

The soma and neurite density imaging (SANDI) model uses a sphere compartment to model the cell soma,  a stick compartment to model the neurite and an isotropic diffusion compartment for the extra-cellular space;  It includes all the tissue parameters in each compartment and a `fracs` vector representing the fraction of  intra-soma signal and intra-neurite signal (the extra-cellular signal fraction is 1-sum(fracs)). For SANDI model, ignore the field of `t2` in all compartments and set them to 0.

# Reference

Palombo, M., Ianus, A., Guerreri, M., Nunes, D., Alexander, D.C., Shemesh, N., Zhang, H., 2020. SANDI: A compartment-based model for non-invasive apparent soma and neurite imaging by diffusion MRI. Neuroimage 215. https://doi.org/10.1016/j.neuroimage.2020.116835
