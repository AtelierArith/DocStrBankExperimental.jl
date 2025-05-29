```
mgslp(A::Matrix{Float64}; tol::Float64 = 1e-12, p::Float64 = 1.0)
```

Modified Gram-Schmidt Process Orthogonalization with ℓᵖ pivoting algorithm (MGSLp)

# Input Arguments

  * `A::Matrix{Float64}`: whose column vectors are to be orthogonalized.

# Output Argument

  * `A::Matrix{Float64}`: orthogonalization matrix of A's column vectors based on ℓᵖ pivoting.
