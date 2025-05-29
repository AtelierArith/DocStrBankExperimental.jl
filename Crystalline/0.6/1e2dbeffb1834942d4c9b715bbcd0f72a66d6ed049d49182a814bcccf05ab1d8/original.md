```julia
struct BandRepSet <: AbstractVector{Crystalline.BandRep}
```

  * `sgnum::Int64`
  * `bandreps::Vector{Crystalline.BandRep}`
  * `kvs::Vector{<:Crystalline.KVec}`
  * `klabs::Vector{String}`
  * `irlabs::Vector{String}`
  * `spinful::Bool`
  * `timereversal::Bool`
