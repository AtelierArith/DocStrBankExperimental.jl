```
SANDIdot(
    soma::Sphere 
    neurite::Stick
    extra::Iso 
    dot::Iso
    fracs::Vector{Float64} 
)
```

SANDIdot model includes additionally a dot compartment for SANDI model; the dot compartment is considered as immobile water and is more commonly seen in ex vivo imaging. For SANDIdot model, ignore the field of t2 in all compartments and set them to 0. The fraction vector represents fractions of the soma,  neurite and dot with the fraction of extra being 1-sum(fracs).

# Reference

Alexander, D.C., Hubbard, P.L., Hall, M.G., Moore, E.A., Ptito, M., Parker, G.J.M., Dyrby, T.B., 2010. Orientationally invariant indices of axon diameter and density from diffusion MRI. Neuroimage 52, 1374–1389. https://doi.org/10.1016/j.neuroimage.2010.05.043

Panagiotaki, E., Schneider, T., Siow, B., Hall, M.G., Lythgoe, M.F., Alexander, D.C., 2012. Compartment models of the diffusion MR signal in brain white matter: A taxonomy and comparison. Neuroimage 59, 2241–2254. 

Palombo, M., Ianus, A., Guerreri, M., Nunes, D., Alexander, D.C., Shemesh, N., Zhang, H., 2020. SANDI: A compartment-based model for non-invasive apparent soma and neurite imaging by diffusion MRI. Neuroimage 215. https://doi.org/10.1016/j.neuroimage.2020.116835
