```
@enum StateCategory
```

Type of a state.

| value     | description                                                                       |
|:--------- |:--------------------------------------------------------------------------------- |
| `XD`      | Differential variable (derivative of variable appears in equations)               |
| `XALG`    | Algebraic variable that is included in x                                          |
| `XLAMBDA` | Algebraic variable that is included in der_x                                      |
| `XMUE`    | Algebraic variable used for stabilization and included in der_x (exact value = 0) |
