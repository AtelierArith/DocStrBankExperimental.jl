```
bregman(A, x, b, options)
```

Linearized bregman iteration for the system

$\frac{1}{2} ||TD \ x||_2^2 + λ ||TD \ x||_{1,w}  \ \ \ s.t Ax = b$

For example, for sparsity promoting denoising (i.e LSRTM)

# Required arguments

  * `A`: Forward operator (e.g. J or preconditioned J for LSRTM)
  * `x`: Initial guess
  * `b`: observed data

# Optional Arguments

  * `callback` : Callback function. Must take as input a `result` callback(x::result)

# Non-required arguments

  * `options`: bregman options, default is bregman_options(); options.TD provides the sparsifying transform (e.g. curvelet), options.w provides the weight vector for the weighted l1
