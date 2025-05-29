@inline function flux*chan*etal(u*ll, u*rr, orientation::Integer,                                            equations::CompressibleEulerEquationsQuasi1D)

Conservative (symmetric) part of the entropy conservative flux for quasi 1D compressible Euler equations split form. This flux is a generalization of [`flux_ranocha`](@ref) for [`CompressibleEulerEquations1D`](@ref). Further details are available in the paper:

  * Jesse Chan, Khemraj Shukla, Xinhui Wu, Ruofeng Liu, Prani Nalluri (2023)  High order entropy stable schemes for the quasi-one-dimensional shallow water and compressible Euler equations [DOI: 10.48550/arXiv.2307.12089](https://doi.org/10.48550/arXiv.2307.12089)
