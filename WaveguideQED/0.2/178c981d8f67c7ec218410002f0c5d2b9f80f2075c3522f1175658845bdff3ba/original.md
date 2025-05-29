```
create(basis::WaveguideBasis{Np,1}) where {Np}
create(basis::WaveguideBasis{Np,Nw},i::Int) where {Np,Nw}
```

Creation operator $w^\dagger$ for [`WaveguideBasis`](@ref) $w_i(t_k)^\dagger | \emptyset \rangle = | 1_k \emptyset \rangle_i$ with cutoff (maximum number of photons Np) where `i` is the index of the waveguide. $t_k$ is determined by the timeindex property of the operator which can be changed by [`set_waveguidetimeindex!(a::WaveguideOperator,k::Int)`](@ref) 

# Arguments

  * basis of type WaveguideBasis, defines cutoff photon number `Np` and number of waveguides `Nw`
  * `i` determines which waveguide the operator acts on and should be `i ≤ Nw`. If `Nw=1` then `i=1` is assumed (there is only one waveguide).

# Returns

[`WaveguideCreate`](@ref)
