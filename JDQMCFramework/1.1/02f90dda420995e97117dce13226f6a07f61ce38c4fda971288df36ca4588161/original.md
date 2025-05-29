```
resize!(
    fgc::FermionGreensCalculator{T,E},
    G::Matrix{T}, logdetG::E, sgndetG::T,
    B::Vector{P}, n_stab::Int
) where {T<:Number, E<:AbstractFloat, P<:AbstractPropagator{T}}

resize!(
    fgc::FermionGreensCalculator{T,E}, n_stab::Int
) where {T,E}
```

Update `fgc` to reflect a new stabilizaiton frequency `n_stab`. If `G`, `logdetG`, `sgndetG` and `B` are also passed then the equal-time Green's function `G` is re-calculated and the corresponding updated values for `(logdetG, sgndetG)` are returned.
