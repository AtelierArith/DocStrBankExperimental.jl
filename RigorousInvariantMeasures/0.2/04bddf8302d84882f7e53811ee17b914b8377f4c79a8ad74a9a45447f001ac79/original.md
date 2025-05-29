```
DiscretizedOperator(B, D; ϵ = 10^(-14), max_iter = 100, T = Float64)
```

Constructor of a discretized operator, it infers if the operator  is integral preserving or not from the basis `B`

Arguments:     B Basis     D Dynamic      ϵ stopping condition for the Newton method     max_iter maximum number of Newton method iterate     T type of the elements stored in the matrix
