```
QuadraticModule{T <: Flag, U <: Flag, B <: AbstractFlagModel{U, N, D}, N, D} <: AbstractFlagModel{T, N, D}
```

Implements quadractic modules for inequalities. Meant to be used as a submodel of a `FlagModel`. Multiplies all elements of the `baseModel` with the `inequality` and then transforms them to type `T` (e.g. by unlabeling). The inequality `f >= 0` is given in form of a `QuantumFlag{U}` describing `f`. If both inequalities `f >= 0` and `-f >= 0` appear in the problem it is equivalent, but much more efficient, to use an `EqualityModule` instead.

# Parameters

  * `T`: Target Flag type
  * `U`: Flag type of the inequality, and the target type of the base model
  * `B`: Type of the base model
  * `N`: Limit parameter, see `AbstractFlagModel`
  * `D`: Data type of coefficients of the final optimization problem
