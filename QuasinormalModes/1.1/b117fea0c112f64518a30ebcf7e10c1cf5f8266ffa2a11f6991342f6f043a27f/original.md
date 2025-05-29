```
computeDelta!(p::QuadraticEigenvalueProblem{N,T}, c::AIMCache{N,Polynomial{T}}) where {N <: Unsigned, T <: Number}
```

Compute and return the AIM "quantization condition".

# Input

  * `m::AIMSteppingMethod`: The stepping method to use.
  * `p::QuadraticEigenvalueProblem`: A quadratic frequency problem.
  * `c::AIMCache`: An AIM cache object created from p.

# Output

An object of type `Polynomial{T}` whose roots are the problem's eigenvalues.
