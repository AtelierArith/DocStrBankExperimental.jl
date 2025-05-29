```
is_pure(ρ :: State) :: Bool
```

Returns `true` if `ρ` is pure, i.e. `rank(ρ) == 1` within the absolute tolerance `ρ.atol`. This method can also be used on `Matrix` types.

```julia
is_pure(ρ :: Matrix; atol=ATOL :: Float64) :: Bool
```
