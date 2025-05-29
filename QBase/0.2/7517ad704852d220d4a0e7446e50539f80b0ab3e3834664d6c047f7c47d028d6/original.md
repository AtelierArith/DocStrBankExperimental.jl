```
is_mixed(ρ :: State) :: Bool
```

Returns `true` if `ρ` is mixed, i.e. `rank(ρ) > 1` within the absolute tolerance `ρ.atol`. This method also can be used on `Matrix` types.

```julia
is_mixed(ρ :: Matrix; atol=ATOL :: Float64) :: Bool
```
