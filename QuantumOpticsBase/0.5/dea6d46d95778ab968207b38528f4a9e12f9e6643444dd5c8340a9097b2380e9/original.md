```
entanglement_entropy(state, partition, [entropy_fun=entropy_vn])
```

Computes the entanglement entropy of `state` between the list of sites `partition` and the rest of the system. The state must be defined in a composite basis.

If `state isa AbstractOperator` the operator-space entanglement entropy is computed, which has the property

```julia
entanglement_entropy(dm(ket)) = 2 * entanglement_entropy(ket)
```

By default the computed entropy is the Von-Neumann entropy, but a different function can be provided (for example to compute the entanglement-renyi entropy).
