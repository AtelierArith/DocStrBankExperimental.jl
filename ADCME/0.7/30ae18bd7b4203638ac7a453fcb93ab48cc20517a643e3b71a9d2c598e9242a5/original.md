```
gradients(ys::PyObject, xs::PyObject; kwargs...)
```

Computes the gradients of `ys` w.r.t `xs`. 

  * If `ys` is a scalar, `gradients` returns the gradients with the same shape as `xs`.
  * If `ys` is a vector, `gradients` returns the Jacobian $\frac{\partial y}{\partial x}$

!!! note
    The second usage is not suggested since `ADCME` adopts reverse mode automatic differentiation.  Although in the case `ys` is a vector and `xs` is a scalar, `gradients` cleverly uses forward mode automatic differentiation, it requires that the second order gradients are implemented for relevant operators.

