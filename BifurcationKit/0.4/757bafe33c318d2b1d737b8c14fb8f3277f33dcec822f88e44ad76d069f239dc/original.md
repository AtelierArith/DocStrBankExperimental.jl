```julia
newton(probPO, orbitguess, options; kwargs...)

```

This is the Newton solver for computing a periodic orbit using orthogonal collocation method. Note that the linear solver has to be apropriately set up in `options`.

# Arguments

Similar to [`newton`](@ref) except that `prob` is a [`PeriodicOrbitOCollProblem`](@ref).

  * `prob` a problem of type `<: PeriodicOrbitOCollProblem` encoding the shooting functional G.
  * `orbitguess` a guess for the periodic orbit.
  * `options` same as for the regular [`newton`](@ref) method.

# Optional argument

  * `jacobian` Specify the choice of the linear algorithm, which must belong to `(AutoDiffDense(), )`. This is used to select a way of inverting the jacobian dG

      * For `AutoDiffDense()`. The jacobian is formed as a dense Matrix. You can use a direct solver or an iterative one using `options`. The jacobian is formed inplace.
      * For `DenseAnalytical()` Same as for `AutoDiffDense` but the jacobian is formed using a mix of AD and analytical formula.
