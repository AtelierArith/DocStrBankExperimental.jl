```
getchemicalattr(chemical::AbstractChemical, attr::Symbol; kwargs...)
getchemicalattr(chemical::AbstractChemical, ::Val{T}; kwargs...)
getchemicalattr(cc::AbstractChemical, ::Val{:formula}; shallow = false, kwargs...)
getchemicalattr(cc::AbstractChemical, ::Val{:elements}; shallow = false, kwargs...)
getchemicalattr(cc::AbstractChemical, ::Val{:charge}; kwargs...)
getchemicalattr(cc::AbstractChemical, ::Val{:abundant_chemical}; kwargs...)
```

Get attribute (`attr`) from `chemical`. This function defaults to take `attr` as a property name, and return the property. If `attr` is not available, it returns `nothing`.

To define specific method for a concrete type `C <: AbstractChemical`, and an attribute (`attr`), use the following function signature:

`getchemicalattr(::C, ::Val{attr}; kwargs...)`
