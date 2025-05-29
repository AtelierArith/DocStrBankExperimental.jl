```
RPCA = rpca(A::Matrix; λ=1.0 / √(maximum(size(A))), iters=1000, tol=1.0e-7, ρ=1.5, verbose=false, nonnegL=false, nonnegS=false, nukeA=true)
```

minimize*{L,D,S} ||L||** + λ||S||₁ + γ||D||₂² s.t. A = L+D+S

Ref: "The Augmented Lagrange Multiplier Method for Exact Recovery of Corrupted Low-Rank Matrices", Zhouchen Lin, Minming Chen, Leqin Wu, Yi Ma, https://people.eecs.berkeley.edu/~yima/psfile/Lin09-MP.pdf

#Arguments:

  * `A`: Input matrix
  * `λ`: Sparsity regularization
  * `iters`: Maximum number of iterations
  * `tol`: Tolerance
  * `ρ`: Algorithm tuning param
  * `verbose`: Print status
  * `nonnegL`: Hard thresholding on A
  * `nonnegS`: Hard thresholding on E
  * `proxL`: NuclearNorm(1/2)
  * `proxD`: nothing
  * `proxS`: NormL1(λ))

To speed up convergence you may either increase the tolerance or increase `ρ`. Increasing `tol` is often the best solution.
