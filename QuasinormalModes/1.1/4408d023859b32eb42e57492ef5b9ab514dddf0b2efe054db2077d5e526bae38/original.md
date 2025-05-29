```
computeDelta!(m::AIMSteppingMethod, p::NumericAIMProblem{N,T}, c::AIMCache{N,T}, ω::T) where {N <: Unsigned, T <: Number}
```

Compute and return the AIM "quantization condition".

# Input

  * `m::AIMSteppingMethod`: The stepping method to use.
  * `p::QuadraticEigenvalueProblem`: A quadratic frequency problem.
  * `c::AIMCache`: An AIM cache object created from p.
  * `ω::T`: Point to evaluate the quantization condition.

# Output

An object of type `T` which represents the AIM quantization condition at point ω.
