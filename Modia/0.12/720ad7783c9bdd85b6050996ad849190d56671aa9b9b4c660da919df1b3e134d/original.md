```
@enum ResidualCategory
```

Type of a residual (see also [`StateCategory`](@ref) for the type of a state).

| value         | description                                                              |
|:------------- |:------------------------------------------------------------------------ |
| `FD`          | Differential equation (depends on XD, XLAMBDA, XMUE variables)           |
| `FC_ALG`      | Constraint equation that is purely algebraic (depends on XALG variables) |
| `FC_LOW_HIGH` | Constraint equation on lowest and on highest derivative level            |
| `FC_MUE`      | Constraint equation that is associated with a stabilizer XMUE            |
