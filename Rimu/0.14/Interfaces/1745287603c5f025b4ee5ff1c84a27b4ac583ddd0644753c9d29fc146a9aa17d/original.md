```
diagonal_element(ham, address)
```

Compute the diagonal matrix element of the linear operator `ham` at address `address`.

# Example

```jldoctest
julia> address = BoseFS((3, 2, 1));


julia> H = HubbardMom1D(address);


julia> diagonal_element(H, address)
8.666666666666664
```

Part of the [`AbstractHamiltonian`](@ref) interface.
