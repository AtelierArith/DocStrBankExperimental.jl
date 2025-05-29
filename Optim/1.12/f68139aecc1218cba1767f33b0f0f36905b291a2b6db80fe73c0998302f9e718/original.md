# Particle Swarm

## Constructor

```julia
ParticleSwarm(; lower = [],
                upper = [],
                n_particles = 0)
```

The constructor takes 3 keywords:

  * `lower = []`, a vector of lower bounds, unbounded below if empty or `-Inf`'s
  * `upper = []`, a vector of upper bounds, unbounded above if empty or `Inf`'s
  * `n_particles = 0`, the number of particles in the swarm, defaults to least three

## Description

The Particle Swarm implementation in Optim.jl is the so-called Adaptive Particle Swarm algorithm in [1]. It attempts to improve global coverage and convergence by switching between four evolutionary states: exploration, exploitation, convergence, and jumping out. In the jumping out state it intentionally tries to take the best particle and move it away from its (potentially and probably) local optimum, to improve the ability to find a global optimum. Of course, this comes a the cost of slower convergence, but hopefully converges to the global optimum as a result.

Note, that convergence is never assessed for ParticleSwarm. It will run until it reaches the maximum number of iterations set in Optim.Options(iterations=x)`.

## References

  * [1] Zhan, Zhang, and Chung. Adaptive particle swarm optimization, IEEE Transactions on Systems, Man, and Cybernetics, Part B: CyberneticsVolume 39, Issue 6 (2009): 1362-1381
