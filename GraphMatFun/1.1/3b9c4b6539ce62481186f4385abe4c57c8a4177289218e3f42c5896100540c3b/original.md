```
normalize!(degopt::Degopt,tp=:row1) -> degopt
```

Normalizes the [`Degopt`](@ref) coefficients, in the way specified by `tp`. If the `tp==:row1` the `degopt` will be transformed to an equivalent [`Degopt`](@ref) with first row equal to `(0 1) (0 1)`.  If `tp==:col1` the first column in the `Ha` and `Hb` matrices will be transformed to zero.
