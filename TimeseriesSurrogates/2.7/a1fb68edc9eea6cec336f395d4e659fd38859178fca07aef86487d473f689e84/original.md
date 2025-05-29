```
AR1(; n_steps, x₀, k, rng)
```

Simple AR(1) model given by the following map:

$$
x(t+1) = k x(t) + a(t),
$$

where $a(t)$ is a draw from a normal distribution with zero mean and unit variance. `x₀` sets the initial condition and `k` is the tunable parameter in the map. `rng` is a random number generator
