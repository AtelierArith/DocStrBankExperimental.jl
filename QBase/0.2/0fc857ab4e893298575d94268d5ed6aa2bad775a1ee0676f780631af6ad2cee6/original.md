```
is_povm( Π :: Vector; atol=ATOL :: Float64 ) :: Bool
```

Returns `true` if `Π` satisfies the following constraints

  * The POVM is complete: `sum(Π) == I`
  * Each POVM element is hermitian
  * Each POVM element positive semi-definite
