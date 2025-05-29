```
flux(M::MPS)

flux(M::MPO)

totalqn(M::MPS)

totalqn(M::MPO)
```

For an MPS or MPO which conserves quantum numbers, compute the total QN flux. For a tensor network such as an MPS or MPO, the flux is the sum of fluxes of each of the tensors in the network. The name `totalqn` is an alias for `flux`.
