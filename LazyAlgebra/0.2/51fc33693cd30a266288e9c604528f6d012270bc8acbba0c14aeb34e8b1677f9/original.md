```
∇(A, x)
```

yields a result corresponding to the Jacobian (first partial derivatives) of the linear mapping `A` for the variables `x`.  If `A` is a linear mapping, `A` is returned whatever `x`.

The call

```
jacobian(A, x)
```

is an alias for `∇(A,x)`.
