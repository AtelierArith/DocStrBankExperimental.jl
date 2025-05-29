Evolve a `State` `ρ` by `Λ` the [`ChoiOp`](@ref) representation of a channel.

```
evolve(Λ ::  ChoiOp, ρ :: State) :: State
evolve(Λ :: ChoiOp, ρ :: AbstractMatrix) :: Matrix
```

See the [`choi_evolve`](@ref) method for details.
