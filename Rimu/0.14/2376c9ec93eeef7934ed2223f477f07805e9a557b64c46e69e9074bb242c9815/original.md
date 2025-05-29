```
default_starting_vector(hamiltonian::AbstractHamiltonian; kwargs...)
default_starting_vector(
    address=starting_address(hamiltonian);
    style=IsDynamicSemistochastic(),
    initiator=NonInitiator(),
    threading=nothing,
    population=10
)
```

Return a default starting vector for [`ProjectorMonteCarloProblem`](@ref). The default choice for the starting vector is

```julia
v = PDVec(address => population; style, initiator)
```

if threading is available, or otherwise

```julia
v = DVec(address => population; style)
```

if `initiator == NonInitiator()`, and

```julia
v = InitiatorDVec(address => population; style, initiator)
```

if not. See [`PDVec`](@ref), [`DVec`](@ref), [`InitiatorDVec`](@ref), [`StochasticStyle`](@ref), and [`InitiatorRule`](@ref).
