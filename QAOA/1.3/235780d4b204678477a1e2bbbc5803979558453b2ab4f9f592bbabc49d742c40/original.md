```
anneal(problem::Problem, schedule::Function, T::Float64)
```

An extra function to do quantum annealing for a given problem instead of the QAOA.

### Input

  * `problem::Problem`: A `Problem` instance defining the optimization problem.
  * `schedule::Function`: A function specifying the annealing schedule (s. below).
  * `T::Float64`: The duration of the annealing run.

### Output

  * `probabilities::Vector{Float64}`: The vector of output probabilities over the bitstrings.

### Notes

The function `schedule` should map from $[0, T]$ to $[0, 1]$ and have `schedule(0) == 0`, `schedule(T) == 1`.  In the simplest case of a linear schedule, set `schedule(t) = t/T`. With driver $\hat H_D$ and problem Hamiltonian $\hat H_P$, the full annealing Hamiltonian then reads

$\hat H_A = (1 - t/T) \hat H_D + (t/T) \hat H_P$
