```
PCEuler(ggprime; theta=1/2, eta=1/2)
```

Predictor Corrector Euler

# Arguments

  * `ggprime::Function`: For scalar problems, `ggprime` $= b\partial_x(b)$ For multi-dimensional problems `bbprime_k` $= \sum_{j=1...M, i=1...D} b^(j)_i \partial_i b^(j)_k$ where $b^(j)$ correspond to the noise vector due to the j'th noise channel. If problem is in place - a in place ggprime should be supplied - and vice versa for not in place speicification of problem.
  * `theta::Real`: Degree of implicitness in the drift term. Set to 0.5 by default.
  * `eta::Real`: Degree of implicitness in the diffusion term. Set to 0.5 by default.

Reference: Stochastics and Dynamics, Vol. 8, No. 3 (2008) 561–581 Note that the original paper has a typo in the definition of ggprime...
