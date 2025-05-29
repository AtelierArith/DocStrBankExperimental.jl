```julia
NoiseWrapper{T, N, Tt, T2, T3, T4, ZType, inplace} <:
AbstractNoiseProcess{T, N, Vector{T2}, inplace}
```

This produces a new noise process from an old one, which will use its interpolation to generate the noise. This allows you to reuse a previous noise process not just with the same timesteps, but also with new (adaptive) timesteps as well. Thus this is very good for doing Multi-level Monte Carlo schemes and strong convergence testing.

## Constructor

```julia
NoiseWrapper(source::AbstractNoiseProcess{T, N, Vector{T2}, inplace};
    reset = true, reverse = false, indx = nothing) where {T, N, T2, inplace}
```

## NoiseWrapper Example

In this example, we will solve an SDE three times:

  * First, to generate a noise process
  * Second, with the same timesteps to show the values are the same
  * Third, with half-sized timesteps

First, we will generate a noise process by solving an SDE:

```julia
using StochasticDiffEq, DiffEqNoiseProcess
f1(u, p, t) = 1.01u
g1(u, p, t) = 1.01u
dt = 1 // 2^(4)
prob1 = SDEProblem(f1, g1, 1.0, (0.0, 1.0))
sol1 = solve(prob1, EM(), dt = dt, save_noise = true)
```

Now we wrap the noise into a NoiseWrapper and solve the same problem:

```julia
W2 = NoiseWrapper(sol1.W)
prob1 = SDEProblem(f1, g1, 1.0, (0.0, 1.0), noise = W2)
sol2 = solve(prob1, EM(), dt = dt)
```

We can test

```julia
@test sol1.u ≈ sol2.u
```

to see that the values are essentially equal. Now we can use the same process to solve the same trajectory with a smaller `dt`:

```julia
W3 = NoiseWrapper(sol1.W)
prob2 = SDEProblem(f1, g1, 1.0, (0.0, 1.0), noise = W3)

dt = 1 // 2^(5)
sol3 = solve(prob2, EM(), dt = dt)
```

We can plot the results to see what this looks like:

```julia
using Plots
plot(sol1)
plot!(sol2)
plot!(sol3)
```

![noise_process](assets/noise_process.png)

In this plot, `sol2` covers up `sol1` because they hit essentially the same values. You can see that `sol3` is similar to the others, because it's using the same underlying noise process, just sampled much finer.

To double-check, we see that:

```julia
plot(sol1.W)
plot!(sol2.W)
plot!(sol3.W)
```

![coupled_wiener](assets/coupled_wiener.png)

the coupled Wiener processes coincide at every other time point, and the intermediate timepoints were calculated according to a Brownian bridge.

### Adaptive NoiseWrapper Example

Here we will show that the same noise can be used with the adaptive methods using the `NoiseWrapper`. `SRI` and `SRIW1` use slightly different error estimators, and thus have slightly different stepping behavior. We can see how they solve the same 2D SDE differently by using the noise wrapper:

```julia
prob = SDEProblem(f1, g1, ones(2), (0.0, 1.0))
sol4 = solve(prob, SRI(), abstol = 1e-8, save_noise = true)

W2 = NoiseWrapper(sol4.W)
prob2 = SDEProblem(f1, g1, ones(2), (0.0, 1.0), noise = W2)
sol5 = solve(prob2, SRIW1(), abstol = 1e-8)

using Plots
plot(sol4)
plot!(sol5)
```

![SRI_SRIW1_diff](assets/SRI_SRIW1_diff.png)
