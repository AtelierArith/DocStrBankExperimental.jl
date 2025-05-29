```
function get_electron_density(
    expname::String,
    snap::Integer,
    expdir::String;
    units::String="si",
    slicex::AbstractVector{<:Integer}=Int[],
    slicey::AbstractVector{<:Integer}=Int[],
    slicez::AbstractVector{<:Integer}=Int[],
    rho::Array{T,3}=Float32[;;;],
    e::Array{T,3}=Float32[;;;],
    tabfile::String="tabparam.in"
    ) where {T<:AbstractFloat}
```
