```
staircasetopology2d(nx::Integer, ny::Integer)
```

Create a 2D staircase topology on a grid of `nx` by `ny` qubits. Mind the order of the topology, which forms a staircase spanning the grid -> in the Schrödinger picture <-.  An observable acting on qubits index `nqubits` may interact non-trivially with every gate on the topology.  Can topology can either be pathological or the most simple, depending on which index observables are non-identity.
