```
createLeafOpticalStruct(λ_bnds)

Loads in the PROSPECT-PRO database of pigments (and other) absorption cross section in leaves, returns a [`LeafOpticalProperties`](@ref) type struct with spectral units attached.
```

# Arguments

```
- `λ_bnds` an array (with or without a spectral grid unit) that defines the upper and lower limits over which to average the absorption cross sections
```

# Examples

```julia-repl
julia> using Unitful                                                               # Need to include Unitful package 
julia> opti = createLeafOpticalStruct((400.0:5:2400)*u"nm");                       # in nm
julia> opti = createLeafOpticalStruct((0.4:0.1:2.4)*u"μm");                        # in μm
julia> opti = CanopyOptics.createLeafOpticalStruct((10000.0:100:25000.0)u"1/cm");  # in wavenumber (cm⁻¹)
```
