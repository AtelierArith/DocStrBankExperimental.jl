```
BFGS_periodic(FJ::Function, x::AbstractVector, q::Integer;
              maxiter::Integer=50)
```

Find a periodic orbit using BFGS from the Optim package.

Arguments:

  * `FJ`: A function that returns the map and its derivative `F, dFdx = FJ(x)`
  * `x`: An initial point to find the orbit from
  * `q`: The period of the orbit
  * `maxiter=50`: The maximum number of optimization steps allows

Output:

  * `xs`: A periodic trajectory of length `d`
  * `res`: An Optim return object, (can check convergence with `Optim.converged(res)`)
