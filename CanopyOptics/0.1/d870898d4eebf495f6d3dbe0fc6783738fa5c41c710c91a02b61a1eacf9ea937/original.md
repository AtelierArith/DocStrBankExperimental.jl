```
prospect(leaf::LeafProspectProProperties{FT},
                optis) where {FT<:AbstractFloat}
```

Computes leaf optical properties (reflectance and transittance) based on PROSPECT-PRO

# Arguments

  * `leaf`  [`LeafProspectProProperties`](@ref) type struct which provides leaf composition
  * `optis` [`LeafOpticalProperties`](@ref) type struct, which provides absorption cross sections and spectral grid

# Examples

```julia-repl
julia> opti = createLeafOpticalStruct((400.0:5:2400)*u"nm");
julia> leaf = LeafProspectProProperties{Float64}(Ccab=30.0);
julia> T,R = prospect(leaf,opti);
```
