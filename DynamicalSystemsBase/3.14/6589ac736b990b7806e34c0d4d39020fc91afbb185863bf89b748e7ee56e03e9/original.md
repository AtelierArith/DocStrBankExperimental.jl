```
DeterministicIteratedMap <: DiscreteTimeDynamicalSystem
DeterministicIteratedMap(f, u0, p = nothing; t0 = 0)
```

A deterministic discrete time dynamical system defined by an iterated map as follows:

$$
\vec{u}_{n+1} = \vec{f}(\vec{u}_n, p, n)
$$

An alias for `DeterministicIteratedMap` is `DiscreteDynamicalSystem`.

Optionally configure the parameter container `p` and initial time `t0`.

For construction instructions regarding `f, u0` see the DynamicalSystems.jl tutorial.
