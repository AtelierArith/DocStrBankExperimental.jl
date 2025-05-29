```
newadd, me = get_offdiagonal(ham, address, chosen)
```

Compute value `me` and new address `newadd` of a single (off-diagonal) matrix element in a Hamiltonian `ham`. The off-diagonal element is in the same column as address `address` and is indexed by integer index `chosen`.

# Example

```jldoctest
julia> addr = BoseFS(3, 2, 1);

julia> H = HubbardMom1D(addr);

julia> get_offdiagonal(H, addr, 3)
(BoseFS{6,3}(2, 1, 3), 1.0)
```

Part of the [`AbstractHamiltonian`](@ref) interface.
