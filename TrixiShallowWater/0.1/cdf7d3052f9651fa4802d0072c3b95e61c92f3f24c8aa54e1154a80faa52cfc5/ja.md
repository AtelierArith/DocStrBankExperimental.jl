```
flux_nonconservative_chen_noelle(u_ll, u_rr,
                                 orientation::Integer,
                                 equations::ShallowWaterEquationsWetDry1D)
```

非対称の二点表面フラックスで、非保守的（ソース）項を離散化します。離散化は保守変数に対して[`hydrostatic_reconstruction_chen_noelle`](@ref)を使用します。

一貫性を確保するために、表面フラックス内で[`Trixi.FluxHydrostaticReconstruction`](@extref)および[`hydrostatic_reconstruction_chen_noelle`](@ref)と一緒に使用する必要があります。

静水圧再構成とその動機に関する詳細は以下にあります。

  * Guoxian Chen and Sebastian Noelle (2017) A new hydrostatic reconstruction scheme based on subcell reconstructions [DOI:10.1137/15M1053074](https://dx.doi.org/10.1137/15M1053074)
