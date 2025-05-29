```
StatefulJacobianOperator(jac_op::JacobianOperator, u, p)
```

Wrapper over a [`JacobianOperator`](@ref) which stores the input `u` and `p` and defines `mul!` and `*` for computing VJPs and JVPs.
