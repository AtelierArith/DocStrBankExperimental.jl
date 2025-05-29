```
pCN(noise::NoiseGrid, ρ; reset=true, rng = Xorshifts.Xoroshiro128Plus(rand(UInt64)))
```

Create a new, but correlated noise process from `noise` and additional entropy with correlation ρ. This update defines an autoregressive process in the space of Wiener (or noise process) trajectories, which can be used as proposal distribution in Metropolis-Hastings algorithms (often called the "preconditioned Crank–Nicolson scheme".)

External links

  * [Preconditioned Crank–Nicolson algorithm on Wikipedia](https://en.wikipedia.org/wiki/Preconditioned_Crank%E2%80%93Nicolson_algorithm)
