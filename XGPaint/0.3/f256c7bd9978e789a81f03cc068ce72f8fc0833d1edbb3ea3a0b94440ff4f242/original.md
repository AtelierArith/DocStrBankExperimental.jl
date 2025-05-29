```
get_cosmology(::Type{T}; h=0.69, Neff=3.04, OmegaK=0.0,
    OmegaM=0.29, OmegaR=nothing, Tcmb=2.7255, w0=-1, wa=0)
```

Construct a background cosmology. This function duplicates the cosmology() function in Cosmology.jl, but with the numeric type specified.

# Arguments:

  * `::Type{T}`: numerical type to use for calculations

# Keywords

  * `h` - Dimensionless Hubble constant
  * `OmegaK` - Curvature density (Ω_k)
  * `OmegaM` - Matter density (Ω_m)
  * `OmegaR` - Radiation density (Ω_r)
  * `Tcmb` - CMB temperature in Kelvin; used to compute Ω_γ
  * `Neff` - Effective number of massless neutrino species; used to compute Ω_ν
  * `w0` - CPL dark energy equation of state; `w = w0 + wa(1-a)`
  * `wa` - CPL dark energy equation of state; `w = w0 + wa(1-a)`

# Example

```julia-repl
julia> get_cosmology(Float32; h=0.7)
Cosmology.FlatLCDM{Float32}(0.7f0, 0.7099147f0, 0.29f0, 8.5307016f-5)
```
