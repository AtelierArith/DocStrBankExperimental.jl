Evolve a `State` `ρ` by the [`KrausChannel`](@ref) `𝒩`.

```
evolve(𝒩 :: KrausChannel, ρ :: State) :: State
evolve(𝒩 :: KrausChannel, ρ :: AbstractMatrix) :: Matrix
```

See the [`kraus_evolve`](@ref) method for details.
