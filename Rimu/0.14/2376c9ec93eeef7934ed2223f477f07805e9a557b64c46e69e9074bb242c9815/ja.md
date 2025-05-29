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

[`ProjectorMonteCarloProblem`](@ref) のデフォルトの開始ベクトルを返します。開始ベクトルのデフォルトの選択は

```julia
v = PDVec(address => population; style, initiator)
```

スレッド処理が利用可能な場合、またはそうでない場合は

```julia
v = DVec(address => population; style)
```

`initiator == NonInitiator()` の場合、そして

```julia
v = InitiatorDVec(address => population; style, initiator)
```

そうでない場合です。 [`PDVec`](@ref), [`DVec`](@ref), [`InitiatorDVec`](@ref), [`StochasticStyle`](@ref), および [`InitiatorRule`](@ref) を参照してください。
