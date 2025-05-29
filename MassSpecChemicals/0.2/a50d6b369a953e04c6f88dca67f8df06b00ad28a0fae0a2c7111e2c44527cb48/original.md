```
getchemicalattr(chemical::Chemical, ::Val{T}; kwargs...)
getchemicalattr(chemical::Chemical, ::Val{:name}; kwargs...)
getchemicalattr(chemical::Chemical, ::Val{:formula}; kwargs...) 
getchemicalattr(chemical::Chemical, ::Val{:elements}; kwargs...)
getchemicalattr(cc::Chemical, ::Val{:charge}; kwargs...)
getchemicalattr(chemical::Chemical, ::Val{:abundant_chemical}; kwargs...)
```

Get attribute (`attr`) from `chemical`. For attributes other than `:name` and `:formula`, it iterates through `chemical.attr`. If no matched attribute name is found, it returns `nothing`.
