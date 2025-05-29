```
offdiagonals(h::AbstractHamiltonian, address)
```

Return an iterator over nonzero off-diagonal matrix elements of `h` in the same column as `address`. Will iterate over pairs `(newaddress, matrixelement)`.

# Example

```jldoctest
julia> address = BoseFS(3,2,1);


julia> H = HubbardReal1D(address);


julia> h = offdiagonals(H, address)
6-element Rimu.Hamiltonians.Offdiagonals{BoseFS{6, 3, BitString{8, 1, UInt8}}, Float64, HubbardReal1D{Float64, BoseFS{6, 3, BitString{8, 1, UInt8}}, 1.0, 1.0}}:
 (fs"|2 3 1⟩", -3.0)
 (fs"|2 2 2⟩", -2.449489742783178)
 (fs"|3 1 2⟩", -2.0)
 (fs"|4 1 1⟩", -2.8284271247461903)
 (fs"|4 2 0⟩", -2.0)
 (fs"|3 3 0⟩", -1.7320508075688772)
```

Part of the [`AbstractHamiltonian`](@ref) interface.

# Extemded help

`offdiagonals` return and iterator of type `<:AbstractOffdiagonals`. It defaults to returning `Offdiagonals(h, a)`

See also [`Offdiagonals`](@ref Main.Hamiltonians.Offdiagonals), [`AbstractOffdiagonals`](@ref Main.Hamiltonians.AbstractOffdiagonals).
