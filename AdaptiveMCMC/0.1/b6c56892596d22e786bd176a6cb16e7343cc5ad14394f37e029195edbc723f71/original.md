```
s = RWMState(x0, [rng, [q!]])
```

Constructor for RWMState (random walk Metropolis state).

# Arguments

  * `x0`: The initial state vector
  * `rng`: Random number generator; default `Random.GLOBAL_RNG`.
  * `q!`: Symmetric proposal distribution; default `randn!`. Called by `q!(rng, u)` which puts a draw to vector `u`

If `s` is `RWMState`, then `s.x` is the current state. New proposal may be drawn to `s.y` by calling `draw!`, and the proposal is accepted by calling `accept!(s)`.
