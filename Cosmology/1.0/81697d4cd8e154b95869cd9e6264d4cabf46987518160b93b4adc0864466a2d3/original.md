```
cosmology(; h = 0.69,
            Neff = 3.04,
            OmegaK = 0,
            OmegaM = 0.29,
            OmegaR = nothing,
            Tcmb = 2.7255,
            w0 = -1,
            wa = 0)
```

# Parameters

  * `h` - Dimensionless Hubble constant
  * `Neff` - Effective number of massless neutrino species; used to compute Ω_ν
  * `OmegaK` - Curvature density (Ω_k)
  * `OmegaM` - Matter density (Ω_m)
  * `OmegaR` - Radiation density (Ω_r)
  * `Tcmb` - CMB temperature in Kelvin; used to compute Ω_γ
  * `w0` - CPL dark energy equation of state; `w = w0 + wa(1-a)`
  * `wa` - CPL dark energy equation of state; `w = w0 + wa(1-a)`

# Examples

```jldoctest
julia> c = cosmology()
Cosmology.FlatLCDM{Float64}(0.69, 0.7099122024007928, 0.29, 8.77975992071536e-5)

julia> c = cosmology(OmegaK=0.1)
Cosmology.OpenLCDM{Float64}(0.69, 0.1, 0.6099122024007929, 0.29, 8.77975992071536e-5)

julia> c = cosmology(w0=-0.9, OmegaK=-0.1)
Cosmology.ClosedWCDM{Float64}(0.69, -0.1, 0.8099122024007929, 0.29, 8.77975992071536e-5, -0.9, 0.0)
```
