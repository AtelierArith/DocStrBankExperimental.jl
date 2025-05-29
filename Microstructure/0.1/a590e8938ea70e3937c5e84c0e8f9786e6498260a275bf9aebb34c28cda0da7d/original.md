```
MTE_SMT(
    axon::Stick = Stick()
    extra::Zeppelin = Zeppelin()
    fracs::Float64 = 0.5
    )
```

This is a model using multi-TE spherical mean technique for lower b-value in vivo imaging. Compartmental T2s are considered.  There is not a specific reference for this model yet, but you can refer to previous work related to this topic:

Kaden, E., Kruggel, F., Alexander, D.C., 2016. Quantitative mapping of the per-axon diffusion coefficients in brain white matter. Magn Reson Med 75, 1752–1763. https://doi.org/10.1002/MRM.25734

Kaden, E., Kelm, N. D., Carson, R. P., Does, M. D., & Alexander, D. C. (2016). Multi-compartment microscopic diffusion imaging. NeuroImage, 139, 346-359.

Veraart, J., Novikov, D.S., Fieremans, E., 2017. TE dependent Diffusion Imaging (TEdDI) distinguishes between compartmental T 2 relaxation times. https://doi.org/10.1016/j.neuroimage.2017.09.030

Gong, T., Tong, Q., He, H., Sun, Y., Zhong, J., Zhang, H., 2020. MTE-NODDI: Multi-TE NODDI for disentangling non-T2-weighted signal fractions from compartment-specific T2 relaxation times. Neuroimage 217. https://doi.org/10.1016/j.neuroimage.2020.116906
