```
doubling_birkhoff_average(h::Function, F::Function, x0::AbstractVector;
                          tol::Number = 1e-10, T_init::Integer=10,
                          T_max::Integer=320)
```

Find the weighted Birkhoff ergodic average of an observable function `h` over a trajectory of the map `F` adaptively.

Arguments:

  * `h`: A function from Rᵈ to Rⁿ, where d is the dimension of the state space and n is the dimension of the observation
  * `F`: The (symplectic) map: a function from Rᵈ to Rᵈ
  * `x0`: The initial point of the trajectory in Rᵈ
  * `tol`: The tolerance by which convergence is judged. If the average does not change by more than `tol` over a doubling, the function returns
  * `T_init`: The initial length of the trajectory considered
  * `T_max`: The maximum trajectory length considered

Output:

  * `ave`: The average of `h` over the trajectory
  * `xs`: The trajectory
  * `hs`: The value of `h` on the trajectory
  * `conv_flag`: `true` iff the averages converged
