```
bregman(funobj, x, options)
```

Linearized bregman iteration for the system

$\frac{1}{2} ||TD \ x||_2^2 + λ ||TD \ x||_{1,w}  \ \ \ s.t Ax = b$

# Required arguments

  * `funobj`: a function that calculates the objective value (`0.5 * norm(Ax-b)^2`) and the gradient (`A'(Ax-b)`)
  * `x`: Initial guess

# Optional Arguments

  * `callback` : Callback function. Must take as input a `result` callback(x::result)

# Non-required arguments

  * `options`: bregman options, default is bregman_options(); options.TD provides the sparsifying transform (e.g. curvelet), options.w provides the weight vector for the weighted l1
