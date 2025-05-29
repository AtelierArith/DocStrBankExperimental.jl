```
ConjugateGradients(d,operators,parameters;<keyword arguments>)
```

Conjugate Gradients following Algorithm 2 from Scales, 1987. The user provides an array of linear operators. Verify that linear operator(s) pass the dot product. See also: [`DotTest`](@ref)

# Arguments

  * `Niter=10` : Number of iterations
  * `mu=0`
  * `tol=1.0e-15`
