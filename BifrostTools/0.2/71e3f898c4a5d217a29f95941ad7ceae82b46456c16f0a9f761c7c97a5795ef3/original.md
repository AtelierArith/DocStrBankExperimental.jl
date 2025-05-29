```
function get_electron_density(
    xp::BifrostExperiment,
    snap::Integer,
    kwargs...)
```

Function to calculate the electron density from a snapshot `snap`. Supports slicing. Gas density `rho` and internal energy `e` are optional arguments and can be passed (but they MUST be in cgs units). If these quantities already exist, passing them will speed up the calculation of electron density.

`kwargs`:     units::String="si",     slicex::AbstractVector{<:Integer}=Int[],     slicey::AbstractVector{<:Integer}=Int[],     slicez::AbstractVector{<:Integer}=Int[],     rho::Array{AbstractFloat,3}=Float32[;;;],     e::Array{AbstractFloat,3}=Float32[;;;],     tabfile::String="tabparam.in"
