```
lattice_with_local_conditions(O::AlgAssAbsOrd,
                              ps::Vector{<: IntegerUnion},
                              Is::Vector{<: AlgAssAbsOrdIdl})
                                                          -> AlgAssAbsOrdIdl
```

Given an order $\mathcal{O}$, a list of primes `ps` and a list of lattices `Is`, return a lattice $M$ such that $M_{p} = I_p$ for the primes $p$ and lattices $I$ in the given lists and $M_q = \mathcal{O}_q$ for primes outside `ps`.
