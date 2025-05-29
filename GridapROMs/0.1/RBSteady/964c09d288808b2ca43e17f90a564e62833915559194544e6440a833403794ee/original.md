```
contraction(basis::AbstractArray,coefficient::AbstractArray) -> AbstractArray
```

Multiplies a reduced basis `basis` by a set of reduced coeffiecients `coefficient`. It acts as a generalized linear combination, since `basis` might have a dimension higher than 2.
