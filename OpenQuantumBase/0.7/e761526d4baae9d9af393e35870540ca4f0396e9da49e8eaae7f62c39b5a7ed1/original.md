```julia
evaluate(H, s)

```

Evaluates a time-dependent Hamiltonian at time `s`, expressed in units of `GHz`. For generic `AbstractHamiltonian` types, it defaults to `H.(s)/2/π`.
