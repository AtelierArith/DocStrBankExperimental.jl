```
implicit_linear(A, b; lsolve=linear_solve, Af=factorize)
```

Make implicit function AD compatible (specifically with ForwardDiff and ReverseDiff). This version is for linear equations Ay = b

# Arguments

  * `A::matrix`, `b::vector`: components of linear system $A y = b$
  * `lsolve::function`: lsolve(A, b). Function to solve the linear system, default is backslash operator.
  * `Af::factorization`: An optional factorization of A, useful to override default factorize, or if multiple linear solves will be performed with same A matrix.
