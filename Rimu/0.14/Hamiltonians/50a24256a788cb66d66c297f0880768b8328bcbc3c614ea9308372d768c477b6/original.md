```
dimension(h::AbstractHamiltonian, addr=starting_address(h))
dimension(h::AbstractObservable, addr)
dimension(addr::AbstractFockAddress)
dimension(::Type{<:AbstractFockAddress})
```

Return the estimated dimension of Hilbert space. May return a `BigInt` number.

When called on an address or address type, the dimension of the linear space spanned by the address type is returned. When called on an `AbstractHamiltonian`, an upper bound on the dimension of the matrix representing the Hamiltonian is returned.

# Examples

```jldoctest
julia> dimension(OccupationNumberFS(1,2,3))
16777216

julia> dimension(HubbardReal1D(OccupationNumberFS(1,2,3)))
28

julia> dimension(BoseFS{200,100})
1386083821086188248261127842108801860093488668581216236221011219101585442774669540

julia> Float64(ans)
1.3860838210861882e81
```

Part of the [`AbstractHamiltonian`](@ref) interface. See also [`BasisSetRepresentation`](@ref).

# Extended Help

The default fallback for `dimension` called on an [`AbstractHamiltonian`](@ref) is to return the dimension of the address space, which provides an upper bound. For new Hamiltonians a tighter bound can be provided by defining a custom method.

When extending [`AbstractHamiltonian`](@ref), define a method for the two-argument form `dimension(h::MyNewHamiltonian, addr)`. For number-conserving Hamiltonians, the function [`Hamiltonians.number_conserving_dimension`](@ref) may be useful.

When extending [`AbstractFockAddress`](@ref), define a method for `dimension(::Type{MyNewFockAddress})`.
