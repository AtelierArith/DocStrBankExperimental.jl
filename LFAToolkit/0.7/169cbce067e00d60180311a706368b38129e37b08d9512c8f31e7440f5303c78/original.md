```julia
Chebyshev(operator)
```

Chebyshev polynomial preconditioner for finite element operators. The Chebyshev semi-iterative method is applied to the matrix $D^{-1} A$, where $D^{-1}$ is the inverse of the operator diagonal.

# Arguments:

  * `operator::Operator`:  finite element operator to precondition
  * `chebyshevtype::ChebyshevType`: Chebyshev type, first, fourth, or opt. fourth kind

# Returns:

  * Chebyshev preconditioner object

# Example:

```jldoctest
# setup
mesh = Mesh2D(1.0, 1.0);
mass = GalleryOperator("mass", 4, 4, mesh);

# preconditioner
chebyshev = Chebyshev(mass);

# verify
println(chebyshev)

# output

chebyshev preconditioner:
1st-kind Chebyshev
eigenvalue estimates:
  estimated minimum 0.2500
  estimated maximum 1.3611
estimate scaling:
  λ_min = a * estimated min + b * estimated max
  λ_max = c * estimated min + d * estimated max
  a = 0.0000
  b = 0.1000
  c = 0.0000
  d = 1.0000
```
