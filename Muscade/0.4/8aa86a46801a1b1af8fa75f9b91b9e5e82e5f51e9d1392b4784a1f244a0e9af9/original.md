```
DirectXUA{OX,OU,IA}
```

A non-linear direct solver for optimisation FEM.

An analysis is carried out by a call with the following syntax:

```
initialstate    = initialize!(model)
stateXUA        = solve(DirectXUA{OX,OU,IA};initialstate,time=0:1.:5)
```

The solver does not yet support interior point methods. 

# Parameters

  * `OX`                0 for static analysis                     1 for first order problems in time (viscosity, friction, measurement of velocity)                     2 for second order problems in time (inertia, measurement of acceleration)
  * `OU`                0 for white noise prior to the unknown load process                     2 otherwise
  * `IA`                0 for XU problems (variables of class A will be unchanged)                     1 for XUA problems

# Named arguments

  * `dbg=(;)`           a named tuple to trace the call tree (for debugging).
  * `verbose=true`      set to false to suppress printed output (for testing).
  * `silenterror=false` set to true to suppress print out of error (for testing) .
  * `initialstate`      a `State`.
  * `time`              an `AbstractRange` of times at which to compute the steps.  Example: 0:0.1:5.
  * `maxiter=50`        maximum number of Newton-Raphson iterations.
  * `maxΔλ=1e-5`        convergence criteria: a norm of the scaled `Λ` increment.
  * `maxΔx=1e-5`        convergence criteria: a norm of the scaled `X` increment.
  * `maxΔu=1e-5`        convergence criteria: a norm of the scaled `U` increment.
  * `maxΔa=1e-5`        convergence criteria: a norm of the scaled `A` increment.
  * `saveiter=false`    set to true so that the output `state` is a vector (over the iterations) of                      vectors (over the steps) of `State`s of the model (for debugging                      non-convergence).

Setting the following flags to `true` will improve the sparsity of the system. But setting a flag to `true` when the condition isn't met causes the Hessian to be wrong, which is detrimental for convergence.                      

  * `Xwhite=false`      `true` if response measurement error is a white noise process.
  * `XUindep=false`     `true` if response measurement error is independant of `U`
  * `UAindep=false`     `true` if `U` is independant of `A`
  * `XAindep=false`     `true` if response measurement error is independant of `A`

# Output

A vector of length equal to that of `time` containing the state of the optimized model at each of these steps.                       

See also: [`solve`](@ref), [`SweepX`](@ref)
