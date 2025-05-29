```
momentum(ham::AbstractHamiltonian)
```

Momentum as a linear operator in Fock space. Pass a Hamiltonian `ham` in order to convey information about the Fock basis. Returns an [`AbstractHamiltonian`](@ref) that represents the momentum operator.

Note: `momentum` is currently only defined on [`HubbardMom1D`](@ref).

# Example

```jldoctest
julia> add = BoseFS((1, 0, 2, 1, 2, 1, 1, 3));


julia> ham = HubbardMom1D(add; u = 2.0, t = 1.0);


julia> mom = momentum(ham);


julia> diagonal_element(mom, add) # calculate the momentum of a single configuration
-1.5707963267948966

julia> v = DVec(add => 10; capacity=1000);


julia> rayleigh_quotient(mom, v) # momentum expectation value for state vector `v`
-1.5707963267948966
```

Part of the [`AbstractHamiltonian`](@ref) interface.
