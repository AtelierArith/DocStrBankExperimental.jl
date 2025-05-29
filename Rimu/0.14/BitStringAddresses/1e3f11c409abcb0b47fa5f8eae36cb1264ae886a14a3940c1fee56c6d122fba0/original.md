```
excitation(addr::SingleComponentFockAddress, creations::NTuple, destructions::NTuple)
```

Generate an excitation on address `addr` by applying `creations` and `destructions`, which are tuples of the appropriate address indices (i.e. [`BoseFSIndex`](@ref) for bosons, or [`FermiFSIndex`](@ref) for fermions).

$$
a^†_{c_1} a^†_{c_2} \ldots a_{d_1} a_{d_2} \ldots |\mathrm{addr}\rangle \to
α|\mathrm{naddr}\rangle
$$

Returns the new address `naddr` and the factor `α`. The value of `α` is given by the square root of the product of mode occupations before destruction and after creation. If the excitation is illegal, returns an arbitrary address and the value `0.0`.

# Example

```jldoctest
julia> f = FermiFS(1,1,0,0,1,1,1,1)
FermiFS{6,8}(1, 1, 0, 0, 1, 1, 1, 1)

julia> i, j, k, l = find_mode(f, (3,4,2,5))
(FermiFSIndex(occnum=0, mode=3, offset=2), FermiFSIndex(occnum=0, mode=4, offset=3), FermiFSIndex(occnum=1, mode=2, offset=1), FermiFSIndex(occnum=1, mode=5, offset=4))

julia> excitation(f, (i,j), (k,l))
(FermiFS{6,8}(1, 0, 1, 1, 0, 1, 1, 1), -1.0)
```

See [`SingleComponentFockAddress`](@ref).
