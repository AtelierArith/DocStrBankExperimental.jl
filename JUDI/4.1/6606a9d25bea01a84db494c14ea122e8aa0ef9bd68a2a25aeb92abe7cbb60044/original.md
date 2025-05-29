```
judiJacobian(F,q)
```

Create a linearized modeling operator from the non-linear modeling operator `F` and the source `q`. `q` can be either a judiVector (point source Jacobian) or a `judiWeight` for extended source modeling. `F` is a full modeling operator including source/receiver projections.

# Examples

1. `F` is a modeling operator without source/receiver projections:  J = judiJacobian(Pr*F*Ps',q)
2. `F` is the combined operator `Pr*F*Ps'`:  J = judiJacobian(F,q)
