```
afps!(f!, x; iters::Int = 5000, vel::Float64 = 0.9, ep::Float64 = 0.01, tol::Float64 = 1e-12, grad_norm=x->maximum(abs,x))
```

solve equation `f(x) = x` according to:

```
`f!` : inplace version of function to find fixed point for, calling `f!(out,x)` should amount to writing `out = f(x)`

`x` : initial condition, ideally it should be close to the final solution

`vel` : amount of Nesterov acceleration in [0,1]

`ep` : learning rate, typically in ]0,1[

`tol` : absolute tolerance on |f(x)-x|

`grad_norm` : function to evaluate the norm for |f(x)-x|
```

returns a named tuple (x, error, iters) where:

```
`x` : is the solution found for f(x)=x

`error` : is the norm of f(x)-x at the solution point

`iters` : total number of iterations performed
```
