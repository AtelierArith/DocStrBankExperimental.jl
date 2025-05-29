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

`adduct_ion`から属性（`attr`）を取得します。デフォルトでは、特別なメソッドなしでコア化学の属性を返します。
