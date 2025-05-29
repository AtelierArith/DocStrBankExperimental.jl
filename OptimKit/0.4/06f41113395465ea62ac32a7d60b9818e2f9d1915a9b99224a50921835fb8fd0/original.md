```
optimize(fg, x, alg;
              precondition=_precondition,
              (finalize!)=_finalize!,
              hasconverged=DefaultHasConverged(alg.gradtol),
              shouldstop=DefaultShouldStop(alg.maxiter),
              retract=_retract, inner=_inner, (transport!)=_transport!,
              (scale!)=_scale!, (add!)=_add!,
              isometrictransport=(transport! == _transport! && inner == _inner))
-> x, f, g, numfg, history
```

Optimize (minimize) the objective function returned as the first value of `fg`, where the second value contains the gradient, starting from a point `x` and using the algorithm `algorithm`, which is an instance of `GradientDescent`, `ConjugateGradient` or `LBFGS`.

Returns the final point `x`, the coresponding function value `f` and gradient `g`, the total number of calls to `fg`, and the history of the gradient norm across the different iterations.

The algorithm is run until either `hasconverged(x, f, g, norm(g))` returns `true` or `shouldstop(x, f, g, numfg, numiter, time)` returns `true`. The latter case happening before the former is considered to be a failure to converge, and a warning is issued.

The keyword arguments are:

  * `precondition::Function`: A function that takes the current point `x` and the gradient `g`   and returns a preconditioned gradient. By default, the identity is used.
  * `finalize!::Function`: A function that takes the final point `x`, the function value `f`,   the gradient `g`, and the iteration number, and returns a possibly modified values for   `x`, `f` and `g`. By default, the identity is used.   It is the user's responsibility to ensure that the modified values do not lead to   inconsistencies within the optimization algorithm.
  * `hasconverged::Function`: A function that takes the current point `x`, the function value `f`,   the gradient `g`, and the norm of the gradient, and returns a boolean indicating whether   the optimization has converged. By default, the norm of the gradient is compared to the   tolerance `gradtol` as encoded in the algorithm instance.
  * `shouldstop::Function`: A function that takes the current point `x`, the function value `f`,   the gradient `g`, the number of calls to `fg`, the iteration number, and the time spent   so far, and returns a boolean indicating whether the optimization should stop. By default,   the number of iterations is compared to the maximum number of iterations as encoded in the   algorithm instance.

Check the README of this package for further details on creating an algorithm instance, as well as for the meaning of the remaining keyword arguments and their default values.

!!! Warning

```
The default values of `hasconverged` and `shouldstop` are provided to ensure continuity
with the previous versions of this package. However, this behaviour might change in the
future.
```

Also see [`GradientDescent`](@ref), [`ConjugateGradient`](@ref), [`LBFGS`](@ref).
