```
ionizationcrosssection(z::Int, shell::Int, energy::AbstractFloat, ::Type{Bote2009})
ionizationcrosssection(ass::AtomicSubShell, energy::AbstractFloat, ty::Type{<:NeXLAlgorithm}=Bote2009)
```

Computes the absolute ionization crosssection (in cm²/e⁻) for the specified AtomicSubShell and electon energy (in eV).

Example:

```
julia> (/)(map(e->NeXLCore.ionizationcrosssection(n"Fe K",e),[10.0e3,20.0e3])...)
0.5672910174711278
```
