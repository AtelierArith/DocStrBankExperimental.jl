```
pwave_superconductor([T=ComplexF64,] lattice::InfiniteSquare; t=1, μ=2, Δ=1)
```

Square lattice $p$-wave superconductor model, defined by the Hamiltonian

$$
    H = -\sum_{\langle i,j \rangle} \left( t c_i^\dagger c_j +
    \Delta c_i c_j + \text{h.c.} \right) - \mu \sum_i n_i,
$$

where $t$ is the hopping amplitude, $\Delta$ specifies the superconducting gap, $\mu$ is the chemical potential, and $n_i = c_i^\dagger c_i$ is the fermionic number operator.
