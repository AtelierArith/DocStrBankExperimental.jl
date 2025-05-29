```
getchemicalattr(adduct_ion::AbstractAdductIon, attr::Symbol; kwargs...)
getchemicalattr(adduct_ion::AbstractAdductIon, val_attr::Val{T}; kwargs...)
getchemicalattr(adduct_ion::AbstractAdductIon, ::Val{:elements}; kwargs...)
getchemicalattr(adduct_ion::AbstractAdductIon, ::Val{:name}; kwargs...)
getchemicalattr(adduct_ion::AbstractAdductIon, ::Val{:formula}; kwargs...)
getchemicalattr(adduct_ion::AbstractAdductIon, ::Val{:kmer}; kwargs...)
getchemicalattr(adduct_ion::AbstractAdductIon, ::Val{:charge}; kwargs...)
getchemicalattr(adduct_ion::AbstractAdductIon, ::Val{:abundant_chemical}; kwargs...)
```

Get attribute (`attr`) from `adduct_ion`. By default, it return attributes of core chemical without specialized methods.
