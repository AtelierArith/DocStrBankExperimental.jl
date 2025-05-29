```
num_offdiagonals(ham, address)
```

Compute the number of number of reachable configurations from address `address`.

# Example

```jldoctest
julia> address = BoseFS((3, 2, 1));


julia> H = HubbardMom1D(address);


julia> num_offdiagonals(H, address)
10
```

Part of the [`AbstractHamiltonian`](@ref) interface.
