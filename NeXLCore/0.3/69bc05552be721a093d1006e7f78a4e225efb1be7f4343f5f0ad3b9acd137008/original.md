Holds basic data about a material including name, composition in mass fraction and optional propreties.

By default, Material assumes nominal terrestrial atomic weights.  However, it is possible to assign custom atomic weights on a per element-basis for non-terrestrial materials.

The mass fraction and atomic weight are immutable but the `Properties` can be modified.

```
Material(
    name::AbstractString,
    massfrac::AbstractDict{Element,U},
    atomicweights::AbstractDict{Element,V} = Dict{Element,Float64}(),
    properties::AbstractDict{Symbol,Any} = Dict{Symbol,Any}(),
) where { U <: AbstractFloat, V <: AbstractFloat }
```

**Properties**

```
:Density # Density in g/cm³
:Description # Human friendly
:Pedigree #  Quality indicator for compositional data ("SRM-XXX", "CRM-XXX", "NIST K-Glass", "Stoichiometry", "Wet-chemistry by ???", "WDS by ???", "???")
:Conductivity = :Insulator | :Semiconductor | :Conductor
:OtherUserProperties # Other properties can be defined as needed
```
