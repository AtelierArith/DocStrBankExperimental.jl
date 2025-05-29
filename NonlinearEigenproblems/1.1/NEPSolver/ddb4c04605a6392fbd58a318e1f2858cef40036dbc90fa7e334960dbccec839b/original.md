```
compute_rf(eltype::Type,nep::NEP,x,inner_solver::InnerSolver;
           y=x, target=zero(T), λ=target,TOL=eps(real(T))*1e3,max_iter=10)
```

Computes the Rayleigh functional of the `nep`, i.e., computes a vector $Λ$ of values $λ$ such that $y^TM(λ)x=0$, using the procedure specified in `inner_solver`. The default behaviour consists of a scalar valued Newton-iteration, and the returned vector has only one element.

The given eltype<:Number is the type of the returned vector.

# Example

This uses `iar` to solve the (scalar) nonlinear problem.

```julia-repl
julia> nep=nep_gallery("dep0");
julia> x=ones(size(nep,1));
julia> s=compute_rf(ComplexF64,nep,x,IARInnerSolver())[1] # Take just first element
-1.186623627962043 - 1.5085094961223182im
julia> x'*compute_Mlincomb(nep,s,x)
-8.881784197001252e-16 + 1.0880185641326534e-14im
```
