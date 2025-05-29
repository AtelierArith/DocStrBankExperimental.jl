# N-GMRES

## Constructor

```julia
NGMRES(;
        alphaguess = LineSearches.InitialStatic(),
        linesearch = LineSearches.HagerZhang(),
        manifold = Flat(),
        wmax::Int = 10,
        ϵ0 = 1e-12,
        nlprecon = GradientDescent(
            alphaguess = LineSearches.InitialStatic(alpha=1e-4,scaled=true),
            linesearch = LineSearches.Static(),
            manifold = manifold),
        nlpreconopts = Options(iterations = 1, allow_f_increases = true),
      )
```

## Description

This algorithm takes a step given by the nonlinear preconditioner `nlprecon` and proposes an accelerated step by minimizing an approximation of the (ll_2) residual of the gradient on a subspace spanned by the previous `wmax` iterates.

N-GMRES was originally developed for solving nonlinear systems [1], and reduces to GMRES for linear problems. Application of the algorithm to optimization is covered, for example, in [2].

## References

[1] De Sterck. Steepest descent preconditioning for nonlinear GMRES optimization. NLAA, 2013. [2] Washio and Oosterlee. Krylov subspace acceleration for nonlinear multigrid schemes. ETNA, 1997.
