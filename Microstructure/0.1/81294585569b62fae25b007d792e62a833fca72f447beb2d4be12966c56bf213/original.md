```
ExCaliber(
    axon::Cylinder,
    extra::Zeppelin,
    dot::Iso,
    fracs::Vector{Float64}
    )
```

ExCaliber is a multi-compartment model for estimating axon diameter. It can be used for ex vivo imaging when the diffusivity in the ISO compartment is set to 0 (dot compatment), and for in vivo imaging if the diffusivity of the ISO compartment is set to free water in tissue (CSF compartment).  

# Reference

Gong, T., Maffei, C., Dann, E., Lee, H.-H., Lee, H., Augustinack, J.C., Huang, S.Y., Haber, S.N., Yendiki, A., 2025. Interplay between MRI-based axon diameter and myelination estimates in macaque and human brain. Imaging Neuroscience. https://doi.org/10.1162/IMAG*A*00576

Fan, Q., Nummenmaa, A., Witzel, T., Ohringer, N., Tian, Q., Setsompop, K., ... & Huang, S. Y. (2020). Axon diameter index estimation independent of fiber orientation distribution using high-gradient diffusion MRI. Neuroimage, 222, 117197.
