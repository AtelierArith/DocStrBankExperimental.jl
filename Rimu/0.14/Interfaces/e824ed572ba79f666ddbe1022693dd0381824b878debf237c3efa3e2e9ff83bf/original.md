```
starting_address(h)
```

Return the starting address for Hamiltonian `h`. When called on an `AbstractMatrix`, `starting_address` returns the index of the lowest diagonal element.

# Example

```jldoctest
julia> address = BoseFS((3, 2, 1));


julia> H = HubbardMom1D(address);


julia> address == starting_address(H)
true
```

Part of the [`AbstractHamiltonian`](@ref) interface.
