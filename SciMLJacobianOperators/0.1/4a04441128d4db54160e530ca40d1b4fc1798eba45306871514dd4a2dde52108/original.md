```
StatefulJacobianNormalFormOperator(vjp_operator, jvp_operator, cache)
```

This constructs a Normal Form Jacobian Operator, i.e. it constructs the operator corresponding to `JᵀJ` where `J` is the Jacobian Operator. This is not meant to be directly constructed, rather it is constructed with `*` on two [`StatefulJacobianOperator`](@ref)s.
