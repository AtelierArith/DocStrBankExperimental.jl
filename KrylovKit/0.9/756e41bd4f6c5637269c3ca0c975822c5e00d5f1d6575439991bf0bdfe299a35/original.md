```
KrylovKit
```

A Julia package collecting a number of Krylov-based algorithms for linear problems, singular value and eigenvalue problems and the application of functions of linear maps or operators to vectors.

KrylovKit accepts general functions or callable objects as linear maps, and general Julia objects with vector like behavior as vectors.

The high level interface of KrylovKit is provided by the following functions:

  * [`linsolve`](@ref): solve linear systems
  * [`eigsolve`](@ref): find a few eigenvalues and corresponding eigenvectors
  * [`geneigsolve`](@ref): find a few generalized eigenvalues and corresponding vectors
  * [`svdsolve`](@ref): find a few singular values and corresponding left and right singular vectors
  * [`exponentiate`](@ref): apply the exponential of a linear map to a vector
  * [`expintegrator`](@ref): exponential integrator for a linear non-homogeneous ODE, computes a linear combination of the `ϕⱼ` functions which generalize `ϕ₀(z) = exp(z)`.
