# O-ACCEL

## Constructor

```julia
OACCEL(;manifold::Manifold = Flat(),
       alphaguess = LineSearches.InitialStatic(),
       linesearch = LineSearches.HagerZhang(),
       nlprecon = GradientDescent(
           alphaguess = LineSearches.InitialStatic(alpha=1e-4,scaled=true),
           linesearch = LineSearches.Static(),
           manifold = manifold),
       nlpreconopts = Options(iterations = 1, allow_f_increases = true),
       ϵ0 = 1e-12,
       wmax::Int = 10)
```

## Description

This algorithm takes a step given by the nonlinear preconditioner `nlprecon` and proposes an accelerated step by minimizing an approximation of the objective on a subspace spanned by the previous `wmax` iterates.

O-ACCEL is a slight tweak of N-GMRES, first presented in [1].

## References

[1] Riseth. Objective acceleration for unconstrained optimization. 2018.
