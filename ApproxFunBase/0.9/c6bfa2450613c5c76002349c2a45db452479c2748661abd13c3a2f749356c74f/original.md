```
λ, V = eigs(BC::Operator, A::Operator, n::Integer; tolerance::Float64=100eps())
```

Compute `n` eigenvalues and eigenvectors of the operator `A`, subject to the boundary conditions `BC`.

# Examples

```jldoctest
julia> #= We compute the spectrum of the second derivative,
          subject to zero boundary conditions.
          We solve this eigenvalue problem in the Chebyshev basis =#

julia> S = Chebyshev();

julia> D = Derivative(S, 2);

julia> BC = Dirichlet(S);

julia> λ, v = ApproxFun.eigs(BC, D, 100);

julia> λ[1:10] ≈ [-(n*pi/2)^2 for n in 1:10] # compare with the analytical result
true
```
