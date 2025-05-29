```
FlagModel{T <: Flag, N, D} <: AbstractFlagModel{T, N, D}
```

A Flag-model with internal Flag type 'T'.

# Parameters

  * `T`: Target Flag type
  * `N`: Limit parameter, see `AbstractFlagModel`
  * `D`: Data type of coefficients of the final optimization problem
