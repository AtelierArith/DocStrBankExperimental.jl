```
DGSEM(; RealT=Float64, polydeg::Integer,
        surface_flux=flux_central,
        surface_integral=SurfaceIntegralWeakForm(surface_flux),
        volume_integral=VolumeIntegralWeakForm(),
        mortar=MortarL2(basis))
```

Create a discontinuous Galerkin spectral element method (DGSEM) using a [`LobattoLegendreBasis`](@ref) with polynomials of degree `polydeg`.
